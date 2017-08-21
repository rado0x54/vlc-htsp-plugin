cmake_minimum_required(VERSION 3.8)
project(vlc_htsp_plugin)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

find_package(LIBVLC REQUIRED)

set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
        src/access.cpp
        src/access.h
        src/discovery.cpp
        src/discovery.h
        src/helper.cpp
        src/helper.h
        src/htsmessage.cpp
        src/htsmessage.h
        src/sha1.c
        src/sha1.h
        src/vlc-htsp-plugin.cpp)

ADD_DEFINITIONS(-D__PLUGIN__ -D_FILE_OFFSET_BITS=64 -D_REENTRANT -D_THREAD_SAFE -DMODULE_STRING=\"htsp\")

INCLUDE_DIRECTORIES(
        ${LIBVLC_INCLUDE_DIR}/vlc
        ${LIBVLC_PLUGIN_INCLUDE_DIR}
)

add_library(htsp_plugin SHARED ${SOURCE_FILES})
target_link_libraries(htsp_plugin ${LIBVLCCORE_LIBRARY})
