cmake_minimum_required(VERSION 3.10 FATAL_ERROR)
# project(FreeCT_wFBP LANGUAGES CXX CUDA)

#set(CMAKE_CXX_STANDARD 14)
#set(CMAKE_CXX_FLAGS "-pthread -Wall")
#set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")
#set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -Og -g")

#find_package(FFTW3 REQUIRED)
#FindCUDA(REQUIRED)
#FindCUDAToolkit(REQUIRED)

file(GLOB SOURCES src/*.cu src/*.cpp)
add_executable(fct_wfbp ${SOURCES})
add_dependencies(fct_wfbp fct_read)

message("${CUDA_LIBRARIES}")
target_include_directories(fct_wfbp PRIVATE include/ ${INCLUDE_DIRS} ${FFTW3_INCLUDE_DIRS})
target_link_libraries(fct_wfbp PRIVATE Boost::system Boost::filesystem ${FFTW3_LIBRARIES} yaml-cpp fct_read cufft)