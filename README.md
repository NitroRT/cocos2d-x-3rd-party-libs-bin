## cocos2d-x externl

add CMake Script for all platforms

## Updated libraries

| Library | Folder | Version | Upstream |
|---|---|---|---|
| rapidjson | `json/` | master `297637bc` (2026-10-29); version macros still read 1.1.0 | https://github.com/Tencent/rapidjson |
| tinyxml2 | `tinyxml2/` | 11.0.0 | https://github.com/leethomason/tinyxml2 |
| xxHash | `xxhash/` | 0.8.4 | https://github.com/Cyan4973/xxHash |
| tinydir | `tinydir/` | 1.2.6 (its package.json still reads 1.2.4) | https://github.com/cxong/tinydir |
| Clipper | `clipper/` | 6.4.2, upstream defaults (`use_lines` on, `use_deprecated` off) | https://sourceforge.net/projects/polyclipping/ |
| zlib | `zlib/`, `win32-specific/zlib/include` | Windows: 1.4 built with `win32/Makefile.msc` (keeps the `zlib1.dll` name that `libcurl.dll` imports). Android, macOS, iOS: system zlib | https://github.com/madler/zlib |

`json/document-wrapper.h` is cocos-specific and is kept across updates.