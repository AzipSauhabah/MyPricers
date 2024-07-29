# MyPricers
Pricers in. c++ multiplatform


# CMake example

This repository is CMake project structure example originally created for XCode project generation.
But it contains valuable insights how to structure your code that it would be easy to maintain using CMake.

## Table of contents
- [Project structure](#project-structure)
- [Running CMake](#running-cmake)
- [Copyright and license](#copyright-and-license)

## Project structure

Project structure is basically one master project with two static libraries.

Insight is that Foo is some kind of project you are working on and deliver as a product.
This Foo product depends on two static libraries A and B which is stand alone libraries without external dependencies.

```
Foo
 ├── CMakeLists.txt
 ├── README.md
 ├── include
 ├── libs
 │   ├── maths
 │   │   ├── CMakeLists.txt
 │   │   ├── include
 │   │   │   └── Phi_JC
 │   │   │       └── Phi_JC.h
 │   │   ├── src
 │   │   │   └── Phi_JC.cpp
 │   │   └── test
 │   │       ├── Phi_JCTests.cpp
 │   │       └── CMakeLists.txt
 │   ├── GBMPath
 │   │   ├── CMakeLists.txt
 │   │   ├── include
 │   │   │   └── GBMPath
 │   │   │       └── GBMPath.h
 │   │   ├── src
 │   │   │   └── GBMPath.cpp
 │   │   └── test
 │   │       ├── GBMPathTests.cpp
 │   │       └── CMakeLists.txt
 │   └── gtest-1.7.0
 │   ├── etc....
 │   │   ├── CMakeLists.txt
 │   │   ├── include
 │   │   │   └── X
 │   │   │       └── X.h
 │   │   ├── src
 │   │   │   └── X.cpp
 │   │   └── test
 │   │       ├── XTest.cpp
 │   │       └── CMakeLists.txt
 │   └── gtest-1.7.0
 ├── src
 │   └── main.cpp
 └── test
```

## Running CMake

To run CMake you need to go into Foo directory and do these steps:

1. Create build directory `mkdir build`.
2. Go into created build directory `cd build`.
3. Run CMake to create XCode project `cmake -G Xcode ../`, but you can create any other project you want.
4. Open XCode project `open Foo.xcodeproj`.

**NOTE**: 
DO NOT make changes to generated project file, instead edit CMakeLists.txt files and regenerate project using CMake.
For example, when you want to add files to project you update CMakeLists.txt to include those files and regenerate build system using CMake.

## Copyright and license

Code and documentation copyright 2024 Azip Sauhabah
