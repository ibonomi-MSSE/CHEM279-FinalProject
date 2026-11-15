cmake_minimum_required (VERSION 3.31)

project (homework_5 LANGUAGES CXX)

# Compiler requirements
set(CMAKE_CXX_STANDARD 20) 
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Find JSON Libraries
find_package(nlohmann_json REQUIRED)
find_package(HDF5 REQUIRED)
find_package(HighFive REQUIRED)
find_package(Armadillo REQUIRED)
find_package(Eigen3 3.4 REQUIRED NO_MODULE)
find_package(BLAS REQUIRED)
find_package(LAPACK REQUIRED)
find_package(chemfiles REQUIRED)

add_library(common INTERFACE)

target_link_libraries(common INTERFACE
    Eigen3::Eigen
    armadillo
    nlohmann_json::nlohmann_json
    HDF5::HDF5
    chemfiles
)

target_compile_definitions(common INTERFACE 
    ARMA_USE_HDF5
    H5_USE_110_API
)

if(CMAKE_SYSTEM_PROCESSOR MATCHES "x86|x86_64|AMD64")
    add_compile_options(-Wa,--gsframe=no)
endif()

link_libraries(common)

# If Needed Make Modifications below this line
set(CMAKE_EXPORT_COMPILE_COMMANDS ON) # For clang-tidy

add_library(functions STATIC
                      include/overlap.cpp
                      include/basis.cpp
                      include/read_xyz.cpp
                      include/fock.cpp
                      include/math.cpp
                      include/gamma.cpp
                      include/scf.cpp
                      include/gradient.cpp
                      ) 
target_include_directories(functions PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include) 
add_executable(CHEM297-FinalProject src/main.cpp)
target_link_libraries(CHEM297-FinalProject PRIVATE functions)
