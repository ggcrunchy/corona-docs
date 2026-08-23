# CoronaMemoryCallbacks

> --------------------- ------------------------------------------------------------------------------------------
> __Revision__			[REVISION_LABEL](REVISION_URL)
> __Keywords__			CORONA_NATIVE_PRODUCT, C, CoronaMemory.h, CoronaMemoryCallbacks
> __See also__			[CoronaMemory.h][native.C.CoronaMemory]
>						[Corona C Functions][native.C]
> --------------------- ------------------------------------------------------------------------------------------


## Overview

WIP WIP WIP

/**
 This structure contains all the callbacks that together make up a memory type interface.
 Many callbacks are optional and may be left `NULL`.
 The C API does not call any of these directly.
*/
typedef struct CoronaMemoryCallbacks {
	// An interface may provide both `getReadableBytes()` and `getWriteableBytes()`; it MUST provide at least one of them.

	/**
	 Optional, but see note above
	 Get the readable memory available from an object through the interface.
	 @param ws Workspace.
	 @param context Used to provide call-specific input to the getter. May be `NULL`, and this must be valid or at least safe.
	 @return Read-only memory corresponding to `object`.
	 It CAN return `NULL`, say if `object` is temporarily invalid or empty, but `getByteCount()` MUST then return 0; conversely,
	 if the latter returns non-0, `getReadableBytes()`'s result MUST point to memory at least satisfying that number of bytes.
	*/
	const void* ( *getReadableBytes )( CoronaMemoryWorkspace *ws );

	/**
	 Optional, but see note above
	 Get the writeable memory available from an object through the interface.
	 The memory might also be readable, but this is at the interface provider's discretion.
	 @param ws Workspace.
	 @param context Used to provide call-specific input to the getter. May be `NULL`, and this must be valid or at least safe.
	 @return Writeable memory corresponding to `object`.
	 `NULL` results are as per `getReadableBytes()`.
	*/
	void* ( *getWriteableBytes )( CoronaMemoryWorkspace *ws );

	/**
	 Required
	 Get the amount of memory available from an object through the interface.
	 @param ws Workspace.
	 @return Number of bytes that may be read from or written to `object`'s memory.
	*/	
	size_t ( *getByteCount )( CoronaMemoryWorkspace *ws );

	/**
	 Optional
	 Update the amount of memory available from an object through the interface.
	 Earlier results of `getReadableBytes()` and `getWriteableBytes()` can be invalidated by this operation.
	 Typically this makes most sense for writeable memory.
	 It is at the interface provider's discretion whether the previous contents are preserved and how new bytes, when `size` is
	 larger than before, are populated.
	 @param ws Workspace.
	 @param size Memory size after resize.
	 @param writeable If non-0, this is intended for `getWriteableBytes()`, else `getReadableBytes()`.
	 On success, a new call to `getByteCount()` must return `size` or larger.
	 Failure must also be robust, e.g. returning 0, or the old size, if the resources are still intact.
	 @param context Used to provide call-specific input to the resize.
	 @return If non-0, success.
	*/
	int ( *resize )( CoronaMemoryWorkspace *ws, size_t size, int writeable );

	// These are fairly specialized routines, and may each be `NULL`: while some special-purpose logic might
	// always check them just to be thorough, it would be too much trouble accounting for these properties on
	// each and every `CoronaMemoryAcquireInterface()` call: as a "good citizen", a memory provider will want
	// to advertise (in the docs, say) when any are valid, so any consumer knows to bother consulting them.

	/**
	 Optional
	 Report any particular memory alignment, say if the object is in shared memory or intended for SIMD operations.
	 @param ws Workspace.
	 @return May be 0 ("normal" memory) or a suitable power of 2.
	*/
	size_t ( *getAlignment )( CoronaMemoryWorkspace *ws );

	/**
	 Optional
	 Query sizes of structured memory, e.g. for texture data 0 = row count, 1 = column count, 2 = bytes per pixel.
	 @param ws Workspace.
	 @param index Zero-based size index.
	 @param size Requested size.
	 @return If non-0, `index` < size count and `dim` must be populated.
	*/
	int ( *getSize )( CoronaMemoryWorkspace *ws, unsigned int index, size_t *size );

	/**
	 Optional
	 Query strides of structured memory, i.e. the number of bytes between successive entries along an axis.
	 Usually the stride will be the product of lower-dimensional sizes, e.g. row-to-row stride = column count * bytes per pixel, but
	 sometimes padding is useful, e.g. for alignment or when using a subregion of memory.
	 @param index Zero-based stride index.
	 @param stride Requested stride.
	 @return If non-0, `index` < stride count and `stride` must be populated.
	*/
	int ( *getStride )( CoronaMemoryWorkspace *ws, unsigned int index, size_t *stride );
} CoronaMemoryCallbacks;
