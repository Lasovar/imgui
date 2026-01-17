cmake_minimum_required(VERSION 3.20)

project(imgui LANGUAGES CXX)

add_library(imgui STATIC)

target_sources(imgui PRIVATE
    imgui.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
    imgui_demo.cpp
)

target_sources(imgui PUBLIC
    imgui.h
    imgui_internal.h
    imconfig.h
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
)

target_include_directories(imgui
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
)

set_target_properties(imgui PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED YES
)

if (UNIX AND NOT APPLE)
    set_target_properties(imgui PROPERTIES POSITION_INDEPENDENT_CODE ON)
endif()
