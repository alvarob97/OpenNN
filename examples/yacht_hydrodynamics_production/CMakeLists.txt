# Specify the minimum version for CMake

cmake_minimum_required(VERSION 2.8.10)

# Project's name

project(yacht_hydrodynamics_production)

if(WIN32)
	if(EXISTS ../../opennn/Release/opennn)
		SET(PROJECT_LINK_LIBS ../../opennn/Release/opennn)
	else()
		SET(PROJECT_LINK_LIBS ../../opennn/Debug/opennn)
	endif()
endif(WIN32)

if(UNIX)
    if(EXISTS ../../opennn/Release/opennn)
		SET(PROJECT_LINK_LIBS ../../opennn/Release/opennn)
	else()
		SET(PROJECT_LINK_LIBS ../../opennn/Debug/opennn)
	endif()
endif(UNIX)

link_directories(${CMAKE_SOURCE_DIR}/opennn)

include_directories(${CMAKE_SOURCE_DIR}/opennn)

add_executable(yacht_hydrodynamics_production main.cpp)

target_link_libraries(yacht_hydrodynamics_production ${PROJECT_LINK_LIBS})
