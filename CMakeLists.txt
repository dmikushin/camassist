cmake_minimum_required(VERSION 3.1)

project(camassist)

file(GLOB SRCS "src/*.cpp" "include/*.h")

find_package(PNG REQUIRED)
find_package(JPEG REQUIRED)

add_library(${PROJECT_NAME} SHARED ${SRCS})
target_compile_definitions(${PROJECT_NAME} PRIVATE FCAM_ARCH_X86)
target_include_directories(${PROJECT_NAME} PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_include_directories(${PROJECT_NAME} PRIVATE ${PNG_INCLUDE_DIRS} ${JPEG_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} ${PNG_LIBRARIES} ${JPEG_LIBRARIES})
