cmake_minimum_required(VERSION 3.12)
set(PROJECT_NAME detect)
set(SRC detect.cpp yolov8.cpp)

project(${PROJECT_NAME}) 

include_directories( 
    "C:/opencv/build/include"
    "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include"
    "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include/ie"
   " C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include/ngraph"
)
 
add_executable(${PROJECT_NAME} ${SRC})
target_link_libraries(${PROJECT_NAME}  
            "C:/opencv/build/x64/vc16/lib/opencv_world480d.lib"
            "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/lib/intel64/Release/openvino.lib"
    )
