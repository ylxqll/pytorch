if(NOT BUILD_ATEN_MOBILE AND BUILD_CAFFE2_OPS)
  # Add source generated by Codegen.cmake and pass to parent
  list(APPEND Caffe2_CPU_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/aten_op.cc)
  list(APPEND Caffe2_GPU_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/aten_op_gpu.cc)
  set(Caffe2_CPU_SRCS ${Caffe2_CPU_SRCS} PARENT_SCOPE)
  set(Caffe2_GPU_SRCS ${Caffe2_GPU_SRCS} PARENT_SCOPE)

  if(USE_ROCM)
    list(APPEND Caffe2_HIP_SRCS ${CMAKE_CURRENT_SOURCE_DIR}/hip/aten_op_gpu.cc)
    set(Caffe2_HIP_SRCS ${Caffe2_HIP_SRCS} PARENT_SCOPE)
  endif()
endif()
