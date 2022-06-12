# SDL2 Statically Linked | Windows 
# @cjens00 https://github.com/cjens00
# Tested on Windows 11 22H2 (22621.1) with
# JetBrains' CLion 2022.1.2 and CMake 3.22

cmake_minimum_required(VERSION 3.8)
project(SDL_STATIC_EXAMPLE)
set(CMAKE_CXX_STANDARD 20)

# Set this to your Windows 10/11 SDK path
# I used the Windows 11 SDK (10.0.22000.0)
set(WindowsSDKDirectory "X:\\Program Files (x86)\\Windows Kits\\10\\Lib\\10.0.22000.0\\um\\x64")
link_directories(${WindowsSDKDirectory})

# The required Windows API libraries to statically link SDL2
if (WIN32)
    add_link_options(imagehlp.lib dinput8.lib dxguid.lib user32.lib gdi32.lib
            winmm.lib imm32.lib ole32.lib oleaut32.lib shell32.lib version.lib uuid.lib Setupapi.lib)
endif ()

# Set this directory to your SDL2 path
set(SDLDirectory "X:\\SDL2")

add_executable(SDL_STATIC_EXAMPLE src/main.cpp)
# target_include_directories(SDL_STATIC_EXAMPLE PRIVATE **include SDL headers here**)
# target_link_libraries(SDL_STATIC_EXAMPLE PRIVATE
#         ${SDLDirectory}/lib/static/SDL2-staticd   <-- Note: These were compiled in Debug mode, for release remove the 'd'
#         ${SDLDirectory}/lib/static/SDL2maind      Also: Change the /lib/static/SDL2... etc path to match yours
#         ${SDLDirectory}/lib/static/SDL2_test)