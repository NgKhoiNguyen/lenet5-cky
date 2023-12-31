# Collect C++ source files
aux_source_directory(. DIR_LIB_SRCS)
aux_source_directory(layer DIR_LIB_SRCS)
aux_source_directory(loss DIR_LIB_SRCS)
aux_source_directory(optimizer DIR_LIB_SRCS)

# Collect CUDA source files
file(GLOB_RECURSE DIR_CUDA_SRCS "layer/*.cu")

# Add the library
add_library(MiniDNNLib ${DIR_LIB_SRCS} ${DIR_CUDA_SRCS})

# Set CUDA-specific flags
set_target_properties(MiniDNNLib PROPERTIES CUDA_SEPARABLE_COMPILATION ON)

# Link CUDA libraries
target_link_libraries(MiniDNNLib CUDA::cudart)
