
cmake_minimum_required(VERSION 3.11 FATAL_ERROR)
project(lzf
    DESCRIPTION ""
    LANGUAGES C)

include(GNUInstallDirs)

add_library(lzf
    # Public headers
    include/lzf.h
    # Private headers
    src/lzfP.h
    # Sources
    src/lzf_c.c
    src/lzf_d.c)
target_include_directories(lzf
    PRIVATE src
    PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>)

install(TARGETS lzf
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
    FILES_MATCHING PATTERN "*.h")

