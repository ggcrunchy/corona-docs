# Numbers in Lua

This guide discusses how numbers are treated in Lua, and Corona in particular. **THIS IS A WORK IN PROGRESS**

<div class="guides-toc">

* [Overview](#overview)
* [The Exponent](#the-exponent-bits)
* [The Fraction](#the-fraction-bits)
* [Special Cases](#special-cases)
* [Exact results](#exact-results)
* [Other Precisions](#other-precisions)
* [Links](#links)

</div>

<a id="overview"></a>

## Overview

Numbers in Corona are 64-bit values, interpreted by Lua 5.1 as double-precision IEEE-754 "float"s. This gives our numbers some flexibility, but comes with a few quirks.

**TODO** +43.75 = 0x4045 e000 0000 0000 = 0 10000000100 010111100000000000000000‬00000000000000000000000000000000

**TODO** -43.75 = 0xc045 e000 0000 0000 = 1 10000000100 010111100000000000000000‬00000000000000000000000000000000

<a id="the-exponent-bits"></a>

## The Exponent Bits

Most of our numbers lie between neighboring powers of 2. For instance, 43.75 follows 32 (2<sup>5</sup>) but comes before 64 (2<sup>6</sup>).

The numbers 43.75 and -43.75 have hexadecimal forms `0x4045e00000000000` and `0xc045e00000000000`, apparently quite similar. In fact, the only difference is that the negative number has its highest bit set. And indeed, this "sign bit" is set aside for exactly this purpose.

What follows will focus on positive numbers, but the analysis is largely the same for negatives.

Our next 11 bits have pattern `10000000100`, or 1028 in decimal. This doesn't seem very helpful, but if we subtract 1023 from it we recover the exponent 5, giving us our interval \[2<sup>5</sup>, 2<sup>6</sup>). Exponents are biased in this way to give us the powers of 2 less than 1&mdash;1/2, 1/4, and so on&mdash;letting us represent ranges from \[2<sup>-1022</sup>, 2<sup>-1021</sup>) at the low end all the way up to \[2<sup>1023</sup>, 2<sup>1024</sup>).

**TODO** this is pretty clumsy still

**TODO** try to convey the scope of these numbers?

<a id="the-fraction-bits"></a>

## The Fraction Bits

The remaining 52 bits have bit pattern `0101111` followed by 45 zeroes, or 1,653,665,488,175,104. Dividing this value by 2<sup>52</sup> gives us our relative position: 0.3671875 of the way along the \[32, 64) interval, exactly what we obtain from (43.75 - 32) / (64 - 32).

If we divvy this interval up, we get a spacing of (64 - 32) / 2<sup>52</sup> = 2<sup>5</sup> / 2<sup>52</sup> = 2<sup>-47</sup>. This is the "unit of least precision" / "unit in the last place", or ulp, for this range. Furthermore, turning this idea around tells us we land exactly on an integer every 2<sup>47</sup> steps, starting from 0: 32, 33, 34...

Doing the same thing with \[64, 128), we can represent values every 1/2<sup>46</sup>th of the way across the range, landing on an integer every 2<sup>46</sup> steps. Notice that our ulp has gotten wider, while our integers are more dense; the "floating point" terminology originates here. **TODO** last comment playing too loose?

The situation with integers prevails all the way to \[2<sup>52</sup>, 2<sup>53</sup>), where we have (2<sup>53</sup> - 2<sup>52</sup>) / 2<sup>52</sup> = 1. In other words, **every** value in that range is an integer, with no gaps.

**TODO** expand one or two of the large powers out for some variety / sense of size?

In \[2<sup>53</sup>, 2<sup>54</sup>), our ulp of 2 is now wide enough to miss: 2<sup>53</sup>, 2<sup>53</sup> + 2, etc. Subsequent ranges only get worse, obviously.

Most of the foregoing applies to negative exponents as well. In the range \[1/8, 1/4), we have (2<sup>-2</sup> - 2<sup>-3</sup>) / 2<sup>52</sup> = 2<sup>-55</sup>. The set of representable values less than 1 is **huge**! We will never land on an integer in this region, of course.

**TODO** in fact, half of all representable values...

<a id="special-cases"></a>

## Special Cases

With 11 bits, we should have 2048 exponents available to us, but our ranges as described above fall short by 2. As it happens, patterns `00000000000` and `11111111111` are set aside for a few special cases.

### All 0s

#### Zero

Nestling numbers between powers of 2 offers plenty of representation, but it leads to quite a glaring omission: **0**!

Numerically speaking, 0's absolute value is less than **any** power. As a result, it won't be found between a consecutive pair of them.

To account for this, we interpret a number as 0 when both its exponent and fraction bits are all 0.

Curiously, the sign bit is **not** required to be 0, so we can end up with a "negative" 0. This is generally unremarkable as far as operations go, but can be surprising when we print the results!

#### Denormals

If only the exponent bits are all 0, we have the so-called denormals.

These are the (0, 2<sup>-1022</sup>) range, with the fraction interpreted as before. Our ulp is 2<sup>-1022</sup> / 2<sup>52</sup> = 4.9406564584124654417656879286822 \* 10<sup>-324</sup>.

### All 1s

The situation goes similarly when the exponent bits are all 1.

#### Infinity

For starters, a fraction of 0 gives us "infinity".

If we divide a vanilla number by infinity, we get 0 back; any other arithmetic results in infinity again. **TODO** double check a couple cases here, maybe expand a bit

We can introduce this value ourselves by dividing by 0, for instance `1 / 0` or `-1 / 0`.

#### Not a Number

A non-0 fraction will give us "Not a Number", often abbreviated as NaN or nan.

These arise from bogus computations like `0 / 0` (a handy way to introduce our own) or where garden-variety numbers are inadequate, such as `math.sqrt(-1)`. Like infinity, NaN is contagious: any arithmetic with one results in another NaN, as will calls to most functions in `math` with NaN arguments.

A NaN has the interesting property of not being equal to any value, including itself. Thus we can detect them like `x ~= x`. This is in fact the only case where this holds in Lua, since primitive equality will supersede any **"eq"** metamethod.

Strictly speaking, we have 2<sup>52</sup> - 1 different NaNs available, though often we only care **whether** we have one. It is not unusual to hijack these 52 bits, storing some data there when our value isn't being used as a number. **TODO** example?

**TODO** quiet / signaling

Apart from 0, with its obvious everyday importance, these special cases often complicate things. Mathematical libraries must go through all sorts of hoops to maintain correctness when they come up. This can slow down code appreciably, enough that many compilers offer "fast math" switches. These will dispense with the handling, avoiding the costs, but it puts the onus on us to provide "nice" numbers.

<a id="exact-results"></a>

## Exact Results

There are **many** values this scheme is able to represent exactly; with the above details in mind, we can even come up with some ourselves.

However, many if not most numbers we type into our editors will be "careless" and inexact. In this case, en route from text to running program, the number will be rounded toward a truly representable value.

**TODO** as factor, e.g. 2<sup>-52</sup> = 2<sup>-2</sup> \* 2<sup>-50</sup>, thus can build up in terms of 1/4ths, (43.75 - 32) = 11.75, which is 47 of them; after multiply by 32, 2<sup>-50</sup> \* 2<sup>5</sup> = 2<sup>-45</sup> for our 45-bit shift (more natural to approach this backward, I think)

**TODO** happens when result of an add, multiply, etc. isn't representable

**TODO** maybe we should walk through an example or two? (e.g. "normal" case; result of computation; incrementing huge numbers)

<a id="other-precisions"></a>

## Other Precisions

### Single Precision

We have been speaking of "double" precision floats. As the name suggests, there is also a single-precision variety. This is a 32-bit value, with 8 bits of exponent&mdash;biased by 127 **CHECK THIS!**&mdash;and 23 devoted to the fraction, with the sign bit as before. These tend to be preferred when memory matters more, such as keeping structures light for cache coherency or when bandwidth is a concern; the obvious downsides are reduced accuracy and numeric range.

### Mobile Shaders

**TODO** the following is still rough, maybe needs some expansion to emphasize where we see issues in practice, e.g. shimmering on certain corners, especially with larger textures

We see doubles in Lua, and often both varieties in native code. Floating point also shows up in Corona's shaders. "High precision fragment shader" support, for instance, comes into play on mobile platforms, and basically boils down to how many bits the driver grants to our numbers in fragment kernels.

According to the OpenGL ES2 specification (see for instance, the "Qualifiers" section [here](https://www.khronos.org/opengles/sdk/docs/reference_cards/OpenGL-ES-2_0-Reference-card.pdf)), "medium" precision&mdash;which is available in both vertex and fragment kernels&mdash;must offer at least 10 bits of fraction: 1024-wide ranges. Furthermore, it promises the swath of values from 2<sup>-14</sup> to 2<sup>14</sup>, suggesting 5 bits of exponent with allowances for the aforementioned special cases. Internally, these will probably be 16-bit values.

With "high" precision&mdash;only guaranteed in the vertex kernel&mdash;we have at least 16 bits fraction: a more generous 65536 slots, plus values from 2<sup>-62</sup> to 2<sup>62</sup>, for 7 bits of exponent.

These sizes are much tighter than their Lua equivalents, especially in medium precision! They arise from various efficiency concerns on mobile. It's quite easy to wander into the ranges where we can only take steps of say 1/8 or 1/4, which can manifest in choppy visuals. Mitigating these effects is a key challenge in authoring shaders.

Even when we're "not using shaders", Corona itself is, in the form of a texture lookup followed by a pixel plot. The lookup coordinates are implemented as floats on the shader side, and occasionally we will see rather mysterious behaviors arise as a result. Larger textures might exhibit shimmering, for instance, on certain edges or corners, as the numbers grow close to 1 and get rounded; thus the call for wider sprite sheet padding on large textures.

**TODO** lowp seem to be 10-bit denormals? not sure if worth including

Although the specification's guarantees leave room for the special cases, mobile hardware will often go the "fast math" route, only supporting 0 and leaving out denormals, infinity, and NaN.

**TODO** could add some snippets to encode paired floats and decode them too (in Lua and shaders both)?

**TODO** conclusion?

<a id="links"></a>

### Links

[What Every Computer Scientist Should Know About Floating-Point Arithmetic](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html)

[The Floating-Point Guide](https://floating-point-gui.de)

[Random ASCII (floating point category)](https://randomascii.wordpress.com/category/floating-point)

[Floating point number representation](https://www.cprogramming.com/tutorial/floating_point/understanding_floating_point_representation.html)

[Demystifying Floating Point Precision](https://blog.demofox.org/2017/11/21/floating-point-precision)

[The Right Way to Calculate Stuff](https://www.plunk.org/~hatch/rightway.php)