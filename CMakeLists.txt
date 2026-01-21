cmake_minimum_required(VERSION 3.22)

# Project name and version
project(MolecularDynamics VERSION 1.0
        DESCRIPTION "Parallelization of an MD code"
        LANGUAGES CXX)

# Add the executable
add_executable(mpimd src/main.cpp)

# Specify the C++ standard
target_compile_features(mpimd PUBLIC cxx_std_11)

# Find MPI
find_package(MPI REQUIRED)
target_link_libraries(mpimd PUBLIC MPI::MPI_CXX)

