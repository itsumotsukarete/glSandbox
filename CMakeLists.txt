cmake_minimum_required(VERSION 4.1)
project(glSandbox)

set(CMAKE_CXX_STANDARD 20)

add_executable(glSandbox src/main.cpp src/glad.c)

target_include_directories(glSandbox PUBLIC 3rdParty/include)


if(CMAKE_SYSTEM_NAME STREQUAL "Windows")
    target_link_directories(glSandbox PUBLIC 3rdParty/lib)
    target_link_libraries(glSandbox glfw3)
    target_link_libraries(glSandbox opengl32)
elseif(CMAKE_SYSTEM_NAME STREQUAL "Linux")
    target_link_directories(glSandbox PUBLIC 3rdParty/lib/Linux)
    find_package(GL)
    target_link_libraries(glSandbox glfw3)
    target_link_libraries(glSandbox GL)

endif ()