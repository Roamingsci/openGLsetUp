cmake_minimum_required(VERSION 3.17)
project(openGLtest1)

set(CMAKE_CXX_STANDARD 11)

#设置一些OpenGL头文件所在目录的宏
#set(GLEW_H /usr/local/Cellar/glew/2.2.0_1/include/GL)
#set(GLFW_H /usr/local/Cellar/glfw/3.3.2/include/GLFW)
set(GLEW_H /usr/local/include/GL)
set(GLFW_H /usr/local/include/GLFW)
set(GLAD_H /usr/local/include/)
set(GLAD_H /usr/local/include/glad)
set(KH_H /usr/local/include/KHR)
#包含上述头文件所在目录
include_directories(${GLEW_H} ${GLFW_H} ${GLAD_H} ${KH_H})

#设置OpenGL库所在位置，并链接
set(GLEW_LINK /usr/local/lib/libGLEW.2.2.0.dylib)
set(GLFW_LINK /usr/local/lib/libglfw.3.4.dylib)
link_libraries(${OPENGL} ${GLEW_LINK} ${GLFW_LINK})

#设置要编译的c/cpp文件到可执行文件中，该exe包含两个文件glad.c,main.cpp,生成SmartPointTest
set(SOURCE_FILES "src/glad.c" "main.cpp")
add_executable(openGLtest1 ${SOURCE_FILES})

# mac下这步很重要
if (APPLE)
    target_link_libraries(openGLtest1 "-framework OpenGL")
    target_link_libraries(openGLtest1 "-framework GLUT")
endif()