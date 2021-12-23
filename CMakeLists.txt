cmake_minimum_required(VERSION 3.20)
project(SPIRV-Reflect LANGUAGES C)

add_library(${PROJECT_NAME} SHARED
	"${CMAKE_CURRENT_SOURCE_DIR}/include/spirv.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/include/spirv_reflect.h"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/spirv_reflect.c"
)
add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_compile_definitions(${PROJECT_NAME} PRIVATE SPV_REFLECT_EXPORTS)

set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME "spirv-reflect")

target_include_directories(${PROJECT_NAME} PUBLIC
	"${CMAKE_CURRENT_SOURCE_DIR}/include/"
)
