cmake_minimum_required(VERSION 3.8)
project(TPProject)

set(CMAKE_CXX_STANDARD 14)
set(PROJECT_VERSION 1.0.0)

SET(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}")
SET(CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${GCC_COVERAGE_LINK_FLAGS}")

include_directories(${CMAKE_SOURCE_DIR}/A)

find_package(PythonInterp 3.6 REQUIRED)
find_package(PythonLibs 3.6 REQUIRED)

execute_process(
 WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}/A"
 COMMAND ${PYTHON_EXECUTABLE} ${CMAKE_SOURCE_DIR}/A/script.py
 COMMENT "Generating enums"
)

set(HEADER_FILES
)

set(SOURCE_FILES
        ${CMAKE_SOURCE_DIR}/main.cpp
	)

add_executable(output ${SOURCE_FILES} ${HEADER_FILES})

