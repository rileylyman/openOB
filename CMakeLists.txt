cmake_minimum_required(VERSION 3.13)
project(OpenOB VERSION 0.0.1)

set(CMAKE_BUILD_TYPE Debug)

add_custom_target(
    bgfx
    COMMAND make linux-release64
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}/external/bgfx/
)

add_subdirectory(external/imgui-lib)

add_executable(OpenOB
    main.cpp
)

add_dependencies(OpenOB
    bgfx
)

target_link_libraries(OpenOB
    ${CMAKE_SOURCE_DIR}/external/bgfx/.build/linux64_gcc/bin/libbgfxRelease.a
    imgui
)


