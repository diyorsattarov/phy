cmake_minimum_required(VERSION 3.5)

project(test)

set(CMAKE_CXX_STANDARD 17)  # Set your desired C++ standard here

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/test/bin)

add_executable(test_main
	test_main.cpp
)

find_package(Qt6 REQUIRED COMPONENTS Widgets)
set(CMAKE_AUTOMOC ON)  # Add this line to enable moc for Qt classes


target_link_libraries(test_main PRIVATE Qt6::Widgets)

add_custom_target(clean_test
    COMMAND ${CMAKE_COMMAND} -E remove_directory ${CMAKE_BINARY_DIR}/test/bin
    COMMAND ${CMAKE_COMMAND} -E remove_directory ${CMAKE_BINARY_DIR}/test/CMakeFiles
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_BINARY_DIR}/test/CMakeCache.txt
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_BINARY_DIR}/test/Makefile
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_BINARY_DIR}/test/cmake_install.cmake
	COMMENT "Cleaning build files"
)