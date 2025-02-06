cmake_minimum_required(VERSION 3.16.0 FATAL_ERROR)

set(CMAKE_SYSTEM_VERSION 10.0 CACHE STRING "" FORCE)

option(STATIC_LINK "Link the application to static Windows library" OFF)

if(STATIC_LINK)
    message("/!\\ Linking Softcam to static Windows /!\\")
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
else()
    message("/!\\ Linking Softcam to dynamic Windows /!\\")
endif()

project(softcam_without_tests CXX)

add_compile_options(/permissive /Zc:strictStrings-)

add_subdirectory(src/baseclasses)
add_subdirectory(src/softcam)
add_subdirectory(src/softcamcore)