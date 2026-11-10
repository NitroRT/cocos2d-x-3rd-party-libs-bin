cmake_minimum_required(VERSION 3.28)

set(lib_name zlib)
set(target_name ext_${lib_name})

project(${lib_name})

include(../cmake/CocosExternalConfig.cmake)

if(MACOSX OR ANDROID)
  add_library(${target_name} INTERFACE)
  target_link_libraries(${target_name} INTERFACE z)
elseif(WINDOWS)
  add_library(${target_name} SHARED IMPORTED GLOBAL)
  set_target_properties(${target_name} PROPERTIES
    INTERFACE_INCLUDE_DIRECTORIES "${CMAKE_CURRENT_SOURCE_DIR}/../win32-specific/zlib/include"
  )
  set_target_properties(${target_name} PROPERTIES
    IMPORTED_LOCATION "${platform_spec_path}/${lib_name}1.dll"
    IMPORTED_IMPLIB "${platform_spec_path}/lib${lib_name}.lib"
  )
endif()

