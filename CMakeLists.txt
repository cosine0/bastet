cmake_minimum_required(VERSION 3.8)
project(bastet)
option(TEST "test build" OFF)
option(DEBUG "debug build" OFF)

set(CMAKE_CXX_STANDARD 14)

set(SOURCE_FILES Ui.cpp Block.cpp Well.cpp BlockPosition.cpp Config.cpp BlockChooser.cpp BastetBlockChooser.cpp JsonSocket.cpp JsonSocket.h)
if (TEST)
    set(SOURCE_FILES Test.cpp ${SOURCE_FILES})
    add_executable(bastet ${SOURCE_FILES})
else ()
    set(SOURCE_FILES main.cpp ${SOURCE_FILES})
    add_executable(bastet ${SOURCE_FILES})
endif ()

if (DEBUG)
    set(CMAKE_BUILD_TYPE Debug)
endif ()

target_link_libraries(bastet ncurses boost_program_options)
