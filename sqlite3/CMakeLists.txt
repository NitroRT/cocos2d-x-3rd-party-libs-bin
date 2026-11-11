cmake_minimum_required(VERSION 3.28)

set(lib_name sqlite3)
set(target_name ext_${lib_name})

project(${lib_name} C)

add_library(${target_name} STATIC
  sqlite3.c
)

target_include_directories(${target_name} PUBLIC .)

target_compile_definitions(${target_name} PRIVATE
  SQLITE_THREADSAFE=1
  SQLITE_DQS=0
)

if(NOT WIN32 AND NOT APPLE AND NOT ANDROID)
  find_package(Threads REQUIRED)
  target_link_libraries(${target_name} PUBLIC Threads::Threads ${CMAKE_DL_LIBS})
endif()

set_target_properties(${target_name}
    PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib"
    FOLDER "External"
)
