cmake_minimum_required(VERSION 3.0.0)
project(final_render VERSION 0.1.0)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
set(CMAKE_CXX_STANDARD 11)

include(CTest)
include(CPack)
enable_testing()

include_directories(inc)

# add the GLFW include path and link the glfw
include_directories(E:\\gllibs\\glfw-3.3.8.bin.WIN64\\include)
link_directories(E:\\gllibs\\glfw-3.3.8.bin.WIN64\\lib-mingw-w64)

# add glm include path
include_directories(E:\\gllibs\\glm-0.9.9.8\\glm)

# opencv part; and the there exits "OpenCVConfig.cmake" file in target file
# elsewise, the following codes fails to work.
set(OpenCV_DIR E:\\gllibs\\opencv)
find_package(OpenCV REQUIRED)
include_directories(E:\\gllibs\\opencv\\include)

add_executable(final_render main.cpp
        src/glad.c
        src/stb_image.cpp
        src/shader.cpp
        src/texture.cpp
        )

target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})
target_link_libraries(${PROJECT_NAME} glfw3.dll)
