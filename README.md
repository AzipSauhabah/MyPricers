<<<<<<< HEAD
# MyPricers
This is a pricer in. c++ multiplatform

# Using CMake example

This repository is CMake project structure example originally created for XCode project generation.
But it contains valuable insights how to structure your code that it would be easy to maintain using CMake.
**NOTE**: 
DO NOT make changes to generated project file, instead edit CMakeLists.txt files and regenerate project using CMake.
For example, when you want to add files to project you update CMakeLists.txt to include those files and regenerate build system using CMake.

=======

# CMake example

This repository is CMake project structure example originally created for XCode project generation.
But it contains valuable insights how to structure your code that it would be easy to maintain using CMake.
>>>>>>> ed03729 (initial commit)

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
<<<<<<< HEAD
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
=======
 │   ├── A
 │   │   ├── CMakeLists.txt
 │   │   ├── include
 │   │   │   └── A
 │   │   │       └── A.h
 │   │   ├── src
 │   │   │   └── A.cpp
 │   │   └── test
 │   │       ├── ATests.cpp
 │   │       └── CMakeLists.txt
 │   ├── B
 │   │   ├── CMakeLists.txt
 │   │   ├── include
 │   │   │   └── B
 │   │   │       └── B.h
 │   │   ├── src
 │   │   │   └── B.cpp
 │   │   └── test
 │   │       ├── BTests.cpp
>>>>>>> ed03729 (initial commit)
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

<<<<<<< HEAD
=======
**NOTE**: 
DO NOT make changes to generated project file, instead edit CMakeLists.txt files and regenerate project using CMake.
For example, when you want to add files to project you update CMakeLists.txt to include those files and regenerate build system using CMake.

>>>>>>> ed03729 (initial commit)
## Copyright and license

Code and documentation copyright 2024 Azip Sauhabah
