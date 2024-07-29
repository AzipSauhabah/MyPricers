cmake_minimum_required(VERSION 3.10)

if(CMAKE_GENERATOR STREQUAL "Xcode")
    set(CMAKE_OSX_SYSROOT "macosx14.5")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGN_IDENTITY "Mac Developer")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGNING_REQUIRED "NO")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGN_ENTITLEMENTS "${CMAKE_SOURCE_DIR}/Entitlements.plist")
endif()

if(CMAKE_GENERATOR STREQUAL "Xcode")
    set(CMAKE_OSX_SYSROOT "macosx14.5")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGN_IDENTITY "Mac Developer")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGNING_REQUIRED "NO")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGN_ENTITLEMENTS "${CMAKE_SOURCE_DIR}/Entitlements.plist")
endif()


# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set C and C++ compilers explicitly if not already set
if(NOT CMAKE_C_COMPILER)
    set(CMAKE_C_COMPILER "/usr/bin/clang")
endif()
if(NOT CMAKE_CXX_COMPILER)
    set(CMAKE_CXX_COMPILER "/usr/bin/clang++")
endif()

# Verify that the specified compilers exist
if(NOT EXISTS ${CMAKE_C_COMPILER})
    message(FATAL_ERROR "Specified C compiler not found: ${CMAKE_C_COMPILER}")
endif()
if(NOT EXISTS ${CMAKE_CXX_COMPILER})
    message(FATAL_ERROR "Specified C++ compiler not found: ${CMAKE_CXX_COMPILER}")
endif()

# Project name and language
project(Foo LANGUAGES CXX)

# Specify the SDK to use
if(CMAKE_GENERATOR STREQUAL "Xcode")
    set(CMAKE_OSX_SYSROOT "macosx14.5")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGN_IDENTITY "Mac Developer")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGNING_REQUIRED "NO")
    set(CMAKE_XCODE_ATTRIBUTE_CODE_SIGN_ENTITLEMENTS "")
endif()

# Source files
set(FOO_SOURCE_DIR src)
set(FOO_SOURCE ${FOO_SOURCE_DIR}/main.cpp)

# Library directories and list of libraries
set(FOO_LIBRARIES_DIR libs)
set(FOO_LIBRARIES A B)

# Include Google Test
enable_testing()
add_subdirectory(${FOO_LIBRARIES_DIR}/gtest-1.7.0)
include_directories(${gtest_SOURCE_DIR}/include)

# Define the executable
add_executable(${PROJECT_NAME} ${FOO_SOURCE})

# Add library directories and link libraries
foreach(LIBRARY ${FOO_LIBRARIES})
    add_subdirectory("${FOO_LIBRARIES_DIR}/${LIBRARY}")
endforeach()
target_link_libraries(${PROJECT_NAME} ${FOO_LIBRARIES})

# Platform-specific settings
if (WIN32)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /W4 /std:c++17")
elseif (APPLE)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra")
elseif (UNIX)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra")
endif()

# Add include directories
target_include_directories(${PROJECT_NAME} PRIVATE ${FOO_SOURCE_DIR})
