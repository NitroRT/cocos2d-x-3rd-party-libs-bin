cmake_minimum_required(VERSION 3.28)

set(lib_name jpeg)
set(target_name ext_${lib_name})

project(${lib_name})

include(../cmake/CocosExternalConfig.cmake)

add_library(${target_name} STATIC IMPORTED GLOBAL)

set_target_properties(${target_name} PROPERTIES
  INTERFACE_INCLUDE_DIRECTORIES "${CMAKE_CURRENT_SOURCE_DIR}/include/${platform_name}"
)
if(WINDOWS)
  set_target_properties(${target_name} PROPERTIES
    IMPORTED_LOCATION "${platform_spec_path}/lib${lib_name}.lib"
  )
elseif(APPLE)
  find_library( JPEG_LIB NAMES libjpeg PATHS ${platform_apple_spec_path} NO_CMAKE_FIND_ROOT_PATH )
  set_target_properties(${target_name} PROPERTIES
    IMPORTED_LOCATION ${JPEG_LIB}
  )
else()
  set_target_properties(${target_name} PROPERTIES
    IMPORTED_LOCATION "${platform_spec_path}/lib${lib_name}.a"
  )
endif()
