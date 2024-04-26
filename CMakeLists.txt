cmake_minimum_required(VERSION 3.12)
set(PROJECT_NAME detect)
set(SRC detect.cpp)

project(${PROJECT_NAME})
find_package(OpenCV REQUIRED)

include_directories(
    ${OpenCV_INCLUDE_DIRS}
    "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include"
    "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include/ie"
   " C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include/ngraph"
)

message(STATUS "OpenCV library status:")
message(STATUS "version:${OpenCV_VERSION}")
message(STATUS "libraries:${OpenCV_LIBS}")
message(STATUS "include path:${OpenCV_INCLUDE_DIRS}")
### generate detector.so
add_library (detector SHARED ${CMAKE_CURRENT_SOURCE_DIR}/yolov8.cpp)
target_include_directories(detector
      PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
      PUBLIC  ${OpenCV_INCLUDE_DIRS}
      "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include"
      "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include/ie"
      "C:/Program Files (x86)/Intel/openvino_2023.3.0/runtime/include/ngraph"
)
target_link_libraries(detector
      ${OpenCV_LIBS}
      "C:/Program Files (x86)/Intel/openvino_2023.3.0//runtime/lib/intel64/Debug/openvinod.lib"
    )

add_executable(${PROJECT_NAME} ${SRC})
target_link_libraries(${PROJECT_NAME} 
            ${OpenCV_LIBS}
            detector
    )
