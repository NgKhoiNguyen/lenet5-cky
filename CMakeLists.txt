cmake_minimum_required (VERSION 3.0)
project (myproject)
find_package(CUDAToolkit REQUIRED)
include_directories(${CUDAToolkit_INCLUDE_DIRS})
include_directories ("${PROJECT_SOURCE_DIR}/third_party/eigen-3.4.0")
enable_language(C CXX CUDA)
aux_source_directory(. DIR_SRCS)
add_subdirectory(src)
add_executable(demo ${DIR_SRCS})
target_link_libraries(demo MiniDNNLib CUDA::cudart)

