message(STATUS "CMAKE_CXX_LINK_LIBRARY_FLAG" ${CMAKE_CXX_LINK_LIBRARY_FLAG})
cmake_minimum_required(VERSION 3.5)

project(CartilageSegmentation LANGUAGES CXX)

set(CMAKE_LINK_LIBRARY_FLAG "")
set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS Core Gui Widgets REQUIRED)

set(SOURCES
    src/main.cpp
    src/occQt.cpp
    src/occqt.qrc
    src/occQt.ui
    src/occView.cpp
)

#Path to OpenCASCADE
set (CASROOT "C:/OpenCASCADE-7.4.0-vc14-64/opencascade-7.4.0")

set(HEADERS
    tmp/
    ${CASROOT}/inc
)

set(OCC_LIBS ${CASROOT}/win64/vc14/lib)

add_definitions(-DNO_COMMONSAMPLE_EXPORTS -DNO_IESAMPLE_EXPORTS -DWNT)

#OpenCascade libs
set(LIBRARIES TKernel TKMath TKG2d TKG3d TKGeomBase TKBRep TKGeomAlgo TKTopAlgo
    TKPrim TKBO TKShHealing TKBool TKHLR TKFillet TKOffset TKFeat TKMesh TKXMesh
    TKService TKV3d TKOpenGl TKMeshVS TKIVtk TKD3DHost TKCDF TKLCAF TKCAF TKBinL
    TKXmlL TKBin TKXml TKStdL TKStd TKTObj TKBinTObj TKXmlTObj TKVCAF TKXSBase
    TKSTEPBase TKSTEPAttr TKSTEP209 TKSTEP TKIGES TKXCAF TKXDEIGES TKXDESTEP TKSTL
    TKVRML TKXmlXCAF TKBinXCAF TKRWMesh TKDraw TKTopTest TKViewerTest TKXSDRAW
    TKDCAF TKXDEDRAW TKTObjDRAW TKQADraw TKIVtkDraw)
link_directories(${OCC_LIBS})
add_executable(${PROJECT_NAME} ${SOURCES})

target_include_directories(${PROJECT_NAME} PRIVATE ${HEADERS} )

#target_link_directories(${PROJECT_NAME} PRIVATE ${OCC_LIBS})

target_link_libraries(${PROJECT_NAME} PRIVATE
    Qt5::Core
    Qt5::Gui
    Qt5::Widgets
    ${LIBRARIES}
)
message(STATUS "CMAKE_CXX_LINK_LIBRARY_FLAG" ${CMAKE_LINK_LIBRARY_FLAG})
