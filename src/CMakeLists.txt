project(planning_main)


#添加目录设置
add_subdirectory(pnc_map)
add_subdirectory(process)

add_executable(${PROJECT_NAME} planning_main.cpp)

#添加头文件与依赖

target_include_directories(${PROJECT_NAME}
PUBLIC
${Process_Dir}
)

target_link_libraries(${PROJECT_NAME}
PUBLIC
process
)