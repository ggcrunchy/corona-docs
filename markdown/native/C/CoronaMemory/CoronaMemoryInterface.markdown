# CoronaMemoryInterface

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryInterface
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

macros...

/**
 Memory operations built atop the user-provided callbacks, provided when the interface has been acquired.
 Always-fail / no-op stubs will be provided for absent callbacks.
*/
typedef struct CoronaMemoryInterface {
	// The following details are found in version 0+:

	/**
	 Passthrough wrapper to `getReadableBytes()`, if available, else returns `NULL`.
	*/
	const void* ( *getReadableBytes )( struct CoronaMemoryAcquireState *state );

	/**
	 If `getReadableBytes()` is absent, returns `NULL`.
	 Otherwise, if the byte count is >= `n`, gets the bytes.
	 Failing that, it will call `resize()`, if present, in read mode.
	 If the resize was successful, gets the bytes; else returns `NULL`.
	*/
	const void* ( *getReadableBytesOfSize )( struct CoronaMemoryAcquireState *state, size_t n );

	/**
	 If `getReadableBytes()` is absent, does nothing.
	 Otherwise, gets the bytes and writes them to `output`, up to a maximum of `outputSize` bytes. If fewer than
	 `outputSize` bytes were available and `ignoreExtra` is 0, the leftover bytes will be set to 0.
	*/
	void ( *copyBytesTo )( struct CoronaMemoryAcquireState *state, void* output, size_t outputSize, int ignoreExtra );

	/**
	 Passthrough wrapper to `getWriteableBytes()`, if available, else returns `NULL`.
	*/
	void* ( *getWriteableBytes )( struct CoronaMemoryAcquireState *state );

	/**
	 If `getWriteableBytes()` is absent, returns `NULL`.
	 Otherwise, if the byte count is >= `n`, gets the bytes.
	 Failing that, it will call `resize()`, if present, in write mode.
	 If the resize was successful, gets the bytes; else returns `NULL`.	 
	*/
	void* ( *getWriteableBytesOfSize )( struct CoronaMemoryAcquireState *state, size_t n );

	/**
	 Passthrough wrapper to `resize()`, if available, else returns 0.
	*/
	int ( *resize )( struct CoronaMemoryAcquireState *state, size_t size, int writeable );

	/**
	 Passthrough wrapper to `getByteCount()`. (As a dummy, returns 0.)
	*/
	size_t ( *getByteCount )( struct CoronaMemoryAcquireState *state );

	/**
	 Passthrough wrapper to `getAlignment()`, if available, else returns 0.
	*/
	size_t ( *getAlignment )( struct CoronaMemoryAcquireState *state );

	/**
	  Passthrough wrapper to `getSize()`, if available, else returns 0.
	*/
	int ( *getSize )( struct CoronaMemoryAcquireState *state, unsigned int index, size_t *size );

	/**
	 Passthrough wrapper to `getStride()`, if available, else returns 0.
	*/
	int ( *getStride )( struct CoronaMemoryAcquireState *state, unsigned int index, size_t *stride );
} CoronaMemoryInterface;
