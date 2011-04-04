cmake_minimum_required(VERSION 2.8)

include_directories (./) 

set (SRC
    eio.c
    eio.h
    xthread.h
    )

add_library (eio ${SRC})

if (__LINUX)
set_property (
    TARGET eio
    PROPERTY COMPILE_DEFINITIONS HAVE_READAHEAD
    )
endif (__LINUX)

install (TARGETS eio ARCHIVE DESTINATION lib)
install (FILES eio.h DESTINATION include)
