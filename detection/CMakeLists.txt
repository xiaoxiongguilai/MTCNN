cmake_minimum_required(VERSION 3.6)
project(MTCNN)

#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_STANDARD 11)

find_package(OpenCV)

SET(OPENCV_INC "/home/hzwangjialei/commlibs/opencv-2.4.13/include")
SET(OPENCV_LIB "/home/hzwangjialei/commlibs/opencv-2.4.13/lib")

include_directories(/home/hzwangjialei/project/ocr_project_2018_02_07/ai-caffe/include ${OPENCV_INC})
include_directories(/home/hzwangjialei/project/ocr_project_2018_02_07/ai-caffe/.build_release/src)
link_directories(/home/hzwangjialei/project/ocr_project_2018_02_07/ai-caffe/build ${OPENCV_LIB})
link_directories(/home/hzwangjialei/project/ocr_project_2018_02_07/ai-caffe/build/lib)

SET(CMAKE_CXX_FLAGS "-lglog -lopencv_core -lopencv_highgui -lopencv_imgproc -lopencv_features2d -lopencv_legacy \
    -lboost_filesystem -lboost_system -std=c++11  -g -O2 -Wall -Wno-sign-compare -D__STDC_CONSTANT_MACROS" )

set(SOURCE_FILES main.cpp MTCNN.cpp MTCNN.h)
add_executable(MTCNN ${SOURCE_FILES})

target_link_libraries(MTCNN ${OpenCV_LIBS} )
target_link_libraries(MTCNN caffe)
