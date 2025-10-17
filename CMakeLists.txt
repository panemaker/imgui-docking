cmake_minimum_required(VERSION 3.4...3.20 FATAL_ERROR)

project(IMGUI VERSION 3.4.0 LANGUAGES C)

add_library(imgui)

target_sources(imgui PRIVATE
                 "${IMGUI_SOURCE_DIR}/misc/cpp/imgui_stdlib.h"
                 "${IMGUI_SOURCE_DIR}/misc/cpp/imgui_stdlib.cpp"
                 "${IMGUI_SOURCE_DIR}/misc/freetype/imgui_freetype.h"
                 "${IMGUI_SOURCE_DIR}/misc/freetype/imgui_freetype.cpp"
                 "${IMGUI_SOURCE_DIR}/imconfig.h"
                 "${IMGUI_SOURCE_DIR}/imgui.h"
                 "${IMGUI_SOURCE_DIR}/imgui.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_demo.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_draw.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_internal.h"
                 "${IMGUI_SOURCE_DIR}/imgui_tables.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_widgets.cpp"
                 "${IMGUI_SOURCE_DIR}/imstb_rectpack.h"
                 "${IMGUI_SOURCE_DIR}/imstb_textedit.h"
                 "${IMGUI_SOURCE_DIR}/imstb_truetype.h"
                 "${IMGUI_SOURCE_DIR}/imgui_stacklayout.cpp"
                 "${IMGUI_SOURCE_DIR}/imgui_stacklayout.h"
                 "${IMGUI_SOURCE_DIR}/imgui_stacklayout_internal.h"
)

if(IMGUI_BACKEND_SDL3)
    target_sources(imgui PRIVATE
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_sdl3.cpp"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_sdl3.h"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_sdlgpu3.cpp"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_sdlgpu3.h"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_sdlgpu3_shaders.h"
    )
elseif(IMGUI_BACKEND_GLFW)
    target_sources(imgui PRIVATE
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_glfw.h"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_glfw.cpp"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3.h"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3.cpp"
                 "${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3_loader.h"
    )
endif()

set(includes
    "${CMAKE_CURRENT_SOURCE_DIR}"
    "${CMAKE_CURRENT_SOURCE_DIR}/backends"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/misc/freetype"
    "${CMAKE_SOURCE_DIR}/external/freetype/include"
)

target_link_libraries(imgui PRIVATE SDL3::SDL3)
target_include_directories(imgui PUBLIC ${includes} )
