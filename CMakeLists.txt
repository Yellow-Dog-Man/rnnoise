cmake_minimum_required(VERSION 3.5)
project(rnnoise)

add_definitions(-DCOMPILE_OPUS)

# Ignore CRT warnings
add_definitions(-D_CRT_SECURE_NO_WARNINGS)

# Get source files
file(GLOB SOURCES "src/*.c" "src/*.h" "include/*.h")

# Build rnnoise
add_definitions(-DRNNOISE_BUILD)

# Build DLL
add_definitions(-DDLL_EXPORT)

# Compile the library
add_library(rnnoise SHARED ${SOURCES})

# Include dirs
target_include_directories(rnnoise PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
        $<INSTALL_INTERFACE:include>
        PRIVATE src)
