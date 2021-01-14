cmake_minimum_required(VERSION 2.8)

project(MazeVisibility)
set(SRC_DIR ${PROJECT_SOURCE_DIR}/src/)
set(INCLUDE_DIR ${PROJECT_SOURCE_DIR}/include/)
set(LIB_DIR ${PROJECT_SOURCE_DIR}/lib/)

include_directories(${INCLUDE_DIR})
include_directories(${LIB_DIR})

add_Definitions("-D_XKEYCHECK_H")
add_definitions(-DPROJECT_DIR="${PROJECT_SOURCE_DIR}")

add_executable(MazeVisibility
    ${SRC_DIR}MapWidget.h
    ${SRC_DIR}MapWidget.cpp
    ${SRC_DIR}Maze.h
    ${SRC_DIR}Maze.cpp
    ${SRC_DIR}MazeWindow.h
    ${SRC_DIR}MazeWindow.cpp
    ${SRC_DIR}RunMaze.cpp)

add_library(MazeLib 
    ${SRC_DIR}Cell.h
    ${SRC_DIR}Cell.cpp
    ${SRC_DIR}Edge.h
    ${SRC_DIR}Edge.cpp
    ${SRC_DIR}LineSeg.h
    ${SRC_DIR}LineSeg.cpp
    ${SRC_DIR}Point.h
    ${SRC_DIR}Vertex.cpp
    ${SRC_DIR}Vertex.h)

target_link_libraries(MazeVisibility 
    debug ${LIB_DIR}Debug/fltk_formsd.lib      optimized ${LIB_DIR}Release/fltk_forms.lib
    debug ${LIB_DIR}Debug/fltk_gld.lib         optimized ${LIB_DIR}Release/fltk_gl.lib
    debug ${LIB_DIR}Debug/fltk_imagesd.lib     optimized ${LIB_DIR}Release/fltk_images.lib
    debug ${LIB_DIR}Debug/fltk_jpegd.lib       optimized ${LIB_DIR}Release/fltk_jpeg.lib
    debug ${LIB_DIR}Debug/fltk_pngd.lib        optimized ${LIB_DIR}Release/fltk_png.lib
    debug ${LIB_DIR}Debug/fltk_zd.lib          optimized ${LIB_DIR}Release/fltk_z.lib
    debug ${LIB_DIR}Debug/fltkd.lib            optimized ${LIB_DIR}Release/fltk.lib)

target_link_libraries(MazeVisibility 
    ${LIB_DIR}OpenGL32.lib
    ${LIB_DIR}glu32.lib)

target_link_libraries(MazeVisibility MazeLib)
    