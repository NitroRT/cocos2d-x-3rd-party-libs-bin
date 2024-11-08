cmake_minimum_required(VERSION 3.28)

set(lib_name glsl_optimizer)
set(target_name ext_${lib_name})

project(${lib_name})

include(../cmake/CocosExternalConfig.cmake)

add_library(ext_glcpp_library STATIC IMPORTED GLOBAL)
add_library(ext_glsl_optimizer STATIC IMPORTED GLOBAL)
add_library(ext_libmesa STATIC IMPORTED GLOBAL)


set_target_properties(${target_name} PROPERTIES
  INTERFACE_INCLUDE_DIRECTORIES "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

find_library( LIBGLCPP_LIB NAMES libglcpp-library PATHS ${platform_apple_spec_path} NO_CMAKE_FIND_ROOT_PATH )
set_target_properties(ext_glcpp_library PROPERTIES
  IMPORTED_LOCATION ${LIBGLCPP_LIB}
)

find_library( LIBGLSL_LIB NAMES libglsl_optimizer PATHS ${platform_apple_spec_path} NO_CMAKE_FIND_ROOT_PATH )
set_target_properties(ext_glsl_optimizer PROPERTIES
  IMPORTED_LOCATION ${LIBGLSL_LIB}
)

find_library( LIBMESA_LIB NAMES libmesa PATHS ${platform_apple_spec_path} NO_CMAKE_FIND_ROOT_PATH )
set_target_properties(ext_libmesa PROPERTIES
  IMPORTED_LOCATION ${LIBMESA_LIB}
)
