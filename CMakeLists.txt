cmake_minimum_required(VERSION 3.0)

#Enable debug symbols
# if (NOT CMAKE_BUILD_TYPE)
#     set(CMAKE_BUILD_TYPE Debug CACHE STRING "Choose debug or release" FORCE)
# endif()

project(SFML_Framework)

set(CMAKE_CXX_STANDARD 14)

# Default mode
IF(NOT CMAKE_CONFIGURATION_TYPES AND NOT CMAKE_BUILD_TYPE)
   SET(CMAKE_BUILD_TYPE RelWithDebInfo)
ENDIF(NOT CMAKE_CONFIGURATION_TYPES AND NOT CMAKE_BUILD_TYPE)
# Select flags.
SET(CMAKE_CXX_FLAGS "-Wall")
SET(CMAKE_CXX_FLAGS_RELWITHDEBINFO "-O2 -g")
SET(CMAKE_CXX_FLAGS_RELEASE "-O2")
SET(CMAKE_CXX_FLAGS_DEBUG  "-O0 -g")

# Add the files
file(GLOB_RECURSE SOURCES Source/*.cpp)
add_executable(framework ${SOURCES})

# Add libraries
# set(SFML_STATIC_LIBRARIES TRUE)
find_package(SFML 2.5 REQUIRED graphics network audio window system)
target_link_libraries(framework sfml-graphics sfml-audio)

# set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++")

#Copy resources
file(COPY ${CMAKE_SOURCE_DIR}/res DESTINATION ${CMAKE_BINARY_DIR})
