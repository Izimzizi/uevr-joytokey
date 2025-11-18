cmake_minimum_required(VERSION 3.20)
project(uevr_joytokey LANGUAGES C CXX)

# Use modern C++
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Grab all the UEVR C/C++ sources in the uevr folder
file(GLOB UEVR_SOURCES
    "uevr/*.c"
    "uevr/*.cpp"
)

# Build a Windows DLL
add_library(uevr-joytokey SHARED
    main.cpp
    ${UEVR_SOURCES}
)

# Include root + uevr headers
target_include_directories(uevr-joytokey PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/uevr
)
