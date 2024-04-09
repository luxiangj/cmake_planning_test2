cmake_minimum_required (VERSION 3.29.0) 
project(planning
    VERSION 0.0.1
    DESCRIPTION "a demo of cmake planning"
    HOMEPAGE_URL https://github.com/luxiangj/cmake_planning_test2
    LANGUAGES CXX 
)
set(CMAKE_CXX_STANDARD 17)
enable_testing()

#添加目录设置
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
set(Process_Dir ${CMAKE_SOURCE_DIR}/src/process)
set(PNC_Map_Dir ${CMAKE_SOURCE_DIR}/src/pnc_map)
set(Show_Result_Dir ${CMAKE_SOURCE_DIR}/src/show_result)


#三方库
set(EIGEN3_INCLUDE_DIR "D:/eigen/eigen-3.4.0")
list(APPEND CMAKE_MODULE_PATH "${EIGEN3_INCLUDE_DIR}/cmake")
message("CMAKE_MODULE_PATH = ${CMAKE_MODULE_PATH}")


find_package(Eigen3 3.4 REQUIRED)

if(TARGET Eigen3::Eigen)
message(STATUS "******** Eigen3 found in ${EIGEN3_INCLUDE_DIR} *********")
endif()


#添加子目录,子目录的Cmakelist也可以用到父目录里的变量
add_subdirectory(src)
add_subdirectory(test/map_test)