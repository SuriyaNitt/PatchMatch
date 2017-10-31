cmake_minimum_required(VERSION 2.8)
project(PatchMatch)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

set(SOURCE_FILES
    source/inpaint.cpp
    source/maskedimage.cpp
    source/nearestneighborfield.cpp
    source/qualitymeasures.cpp
    )


include_directories(
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)


add_executable(patch_match source/main.cpp ${SOURCE_FILES} ${TEST_FILES})


# EXTERNAL LIBRAIRIES =====================

# OpenCV
FIND_PACKAGE(OpenCV 3.1 REQUIRED)
INCLUDE_DIRECTORIES(${OpenCV_INCLUDE_DIRS})
set(TARGET_LIBS ${TARGET_LIBS} ${OpenCV_LIBS})

TARGET_LINK_LIBRARIES(patch_match ${TARGET_LIBS})
