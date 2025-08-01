# System Bindings for libminimap2
Use this if you need lower-level bindings for minimap2.

# Minimap2 Version
Minimap2 2.28

## Breaking Changes
### 0.1.29
Potentially an issue, derive(copy) is no longer valid for structs where we have implemented a Drop trait. So I've added some newtypes where appropriate. Hopefully it's an invisible change.
This is primarily for mm_idx_t. If you use it directly (instead of MmIdx newtype), you need to call mm_idx_destroy() manually.

### 0.1.18
mm2-fast and minimap2 have diverged. At this point mm2-fast is no longer supported. Please use a previous crate version.

## Features 
* vendored - Regenerate the bindings from the vendored minimap2 source. Requires llvm installed. Useful to update the bindings to a different version of minimap2.
* simde - Enable simde support (SIMD-everywhere)
* sse - Enable some sse bindings
* zlib-ng - Use zlib-ng
* static - Static compilation

## TODO
* Can we decouple from pthread? This would allow Windows and (possibly) WASM compilation.

## Changelog
### 0.1.29 minimap2.2.29
* Update to minimap2 2.29
* Update to 2024 edition
* Remove some noise from the build system
* Remove Drop impl for mm_idx_t. If you use it directly (instead of MmIdx newtype), you need to call mm_idx_destroy() manually.

### 0.1.21 minimap2.2.28
* Flag functions for IdxOpt and MapOpt @dwpeng
* Syntactic sugar for mm_idx_t to support Drop, Deref, and DerefMut

### 0.1.20 minimap2.2.28
* Move Drop impl to -sys crate

### 0.1.19 minimap2.2.28
* Update to minimap2 2.28

### 0.1.18 minimap2.2.27
* Regenerated bindings
* mm2-fast and minimap2 have diverged

### 0.1.17 minimap2.2.27
* Updated to newest version of minimap2 @jguhlin
* mm2-fast also received some updates
* Updated deps, rebuilt bindings @jguhlin

### 0.1.16 minimap2.2.26
* Much better cross-compilation support thanks for @Adoni5

### 0.1.15 minimap2.2.26
* Huge thanks to @leiste375 for aarch64 compilation!
* Better static linking support

### 0.1.14 minimap2.2.26
 * Fix regression by reverting to minimap2 release version

### 0.1.13 minimap2.2.26
 * Possible fixes for aarch64 compilation
 * Cleaner build system
 * Early support for cross crate for cross compilation

### 0.1.12 minimap2.2.26
 * Fix bug with SSE2/SSE4...
 
### 0.1.11 minimap2.2.26
* More transparent versioning of upstream minimap2
* Update minimap2-sys minimap2 to release 2.26
* minimap2-sys: update libc, bindgen deps
* Better sse support. Renamed sse flag to sse2only, sse4.1 is otherwise enabled by default (if detected)
* Hopefully better macos, aarch64, and NEON support

### 0.1.10
* Fix bug relating to compiling mm2-fast 

### 0.1.9
* Enable SIMD-everywhere compilation support

### 0.1.8
* Changed how zlib is compiled
* Dep versions update
* Added SSE compilation feature (Mostly autodetects)

### 0.1.7
* Make bindgen an optional feature
* zlib support for musl builds
