cmake_minimum_required(VERSION 3.0)

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
if(WIN32)
   set(SFML_STATIC_LIBRARIES TRUE)
endif(WIN32)
find_package(SFML 2.5 REQUIRED graphics network audio window system)
target_link_libraries(framework sfml-graphics sfml-audio)

# set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++")

#Copy resources
file(COPY ${CMAKE_SOURCE_DIR}/res DESTINATION ${CMAKE_BINARY_DIR})
if(WIN32)
   # Copy DLLs
   file(GLOB_RECURSE BINARY_DEP_DLLS
    "${CMAKE_SOURCE_DIR}/bin/*.dll"
   )
   file(COPY ${BINARY_DEP_DLLS} DESTINATION ${CMAKE_BINARY_DIR})
endif(WIN32)