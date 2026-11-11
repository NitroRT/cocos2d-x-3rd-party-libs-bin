## cocos2d-x externl

add CMake Script for all platforms

## Updated libraries

| Library | Folder | Version | Upstream |
|---|---|---|---|
| rapidjson | `json/` | master `297637bc` (2026-10-29); version macros still read 1.1.0 | https://github.com/Tencent/rapidjson |
| tinyxml2 | `tinyxml2/` | 11.0.0 | https://github.com/leethomason/tinyxml2 |
| xxHash | `xxhash/` | 0.8.4 | https://github.com/Cyan4973/xxHash |
| tinydir | `tinydir/` | 1.2.6 (its package.json still reads 1.2.4) | https://github.com/cxong/tinydir |
| SQLite | `sqlite3/` | 3.54.1 amalgamation (sqlite-amalgamation-3540100.zip, SHA3-256 92281c86...8e30), built from source; off by default, enable with `-DBUILD_EXT_SQLITE=ON` (target `ext_sqlite3`) | https://sqlite.org |
| Clipper | `clipper/` | 6.4.2, upstream defaults (`use_lines` on, `use_deprecated` off) | https://sourceforge.net/projects/polyclipping/ |
| libpng | `png/` | 1.6.59 on Android (arm64-v8a with NEON, armeabi-v7a), Windows (x64, Win32, static `/MD`), Apple xcframework (macos-arm64 15.0, ios-arm64 and ios-arm64-simulator 16.0, NEON, system zlib) | https://github.com/pnggroup/libpng |
| FreeType | `freetype2/` | 2.15.0 on Android (arm64-v8a, armeabi-v7a), Windows (x64, Win32, static `/MD`) and Apple xcframework (macos-arm64 15.0, ios-arm64 and ios-arm64-simulator 16.0), all FT_DISABLE_* on (bundled inflate, no bzip2/png/harfbuzz/brotli/hvf) | https://github.com/freetype/freetype |
| libjpeg-turbo | `jpeg/` | 3.2.1, libjpeg API 62 with `jpeg_mem_src`/`jpeg_mem_dest`, static, no TurboJPEG API. Android arm64-v8a/armeabi-v7a with NEON SIMD; Windows x64/Win32 without SIMD (no NASM; dev target), `/MD`; Apple xcframework (macos-arm64 15.0, ios-arm64 and ios-arm64-simulator 16.0) with NEON SIMD | https://github.com/libjpeg-turbo/libjpeg-turbo |
| libwebp | `webp/` | 1.6.0 decoder only (`libwebpdecoder`, shipped as `libwebp`; headers `decode.h`, `types.h`), threading on, static. Android arm64-v8a/armeabi-v7a with NEON; Windows x64/Win32 with SSE2/SSE4.1, `/MD`; Apple xcframework (macos-arm64 15.0, ios-arm64 and ios-arm64-simulator 16.0) with NEON | https://github.com/webmproject/libwebp |
| zlib | `zlib/` (Windows headers in `zlib/include`) | Windows: 1.4 built with `win32/Makefile.msc`, which keeps zlib's official `zlib1.dll` name. Android, macOS, iOS: system zlib | https://github.com/madler/zlib |

`json/document-wrapper.h` is cocos-specific and is kept across updates.

## Releasing a tag

`version.json` → `prebuilt_libs_version` must equal the tag name. `download-deps.py` compares it with `"version"` in the engine's `external/config.json` to decide whether `external/` is up to date, so commit the new value first, then tag that commit.