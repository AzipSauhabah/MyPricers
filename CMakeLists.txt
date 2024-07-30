cmake_minimum_required(VERSION 3.10)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)

project(Foo LANGUAGES CXX)

# Spécifier les options de la bibliothèque de temps d'exécution pour votre projet principal
if(MSVC)
    # Utiliser /MTd pour les configurations de type Debug
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreadedDebug")
    # Utiliser /MT pour les configurations de type Release
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded")
endif()

# Spécifier l'option /NODEFAULTLIB pour exclure la bibliothèque par défaut 'LIBCMTD'
if(MSVC)
    set(CMAKE_EXE_LINKER_FLAGS_DEBUG "${CMAKE_EXE_LINKER_FLAGS_DEBUG} /NODEFAULTLIB:LIBCMTD")
    set(CMAKE_SHARED_LINKER_FLAGS_DEBUG "${CMAKE_SHARED_LINKER_FLAGS_DEBUG} /NODEFAULTLIB:LIBCMTD")
    set(CMAKE_MODULE_LINKER_FLAGS_DEBUG "${CMAKE_MODULE_LINKER_FLAGS_DEBUG} /NODEFAULTLIB:LIBCMTD")
endif()


# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)

# Set C and C++ compilers explicitly if not already set
if(UNIX)
    if (CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
        set(CMAKE_C_COMPILER "clang")
        set(CMAKE_CXX_COMPILER "clang++")
    else()
        set(CMAKE_C_COMPILER "gcc")
        set(CMAKE_CXX_COMPILER "g++")
    endif()
endif()

if(APPLE)
    # Replace /usr/local/bin/g++ with the full path to your g++ compiler
    set(CMAKE_CXX_COMPILER "/usr/local/bin/g++")
else()
    # Optionally set compiler for other platforms or leave it to default
    # set(CMAKE_CXX_COMPILER "g++")
endif()

# Include Google Test
enable_testing()
add_subdirectory(libs/googletest-1.15.0)
include_directories(${gtest_SOURCE_DIR}/include)

# Source files
set(FOO_SOURCE_DIR src)
set(FOO_SOURCE ${FOO_SOURCE_DIR}/main.cpp)

# Define the executable
add_executable(${PROJECT_NAME} ${FOO_SOURCE})

# Add library directories and link libraries
set(FOO_LIBRARIES A B)  # Replace with actual library names
foreach(LIBRARY ${FOO_LIBRARIES})
    add_subdirectory(libs/${LIBRARY})
    target_link_libraries(${PROJECT_NAME} ${LIBRARY})
endforeach()

# Platform-specific settings
if (WIN32)
    target_compile_options(${PROJECT_NAME} PRIVATE /W4)
elseif (APPLE)
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra)
elseif (UNIX)
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra)
endif()

# Add include directories
target_include_directories(${PROJECT_NAME} PRIVATE ${FOO_SOURCE_DIR})
