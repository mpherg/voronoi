cmake_minimum_required(VERSION 3.15)

project(voronoi CXX)

find_package(Boost REQUIRED COMPONENTS program_options)
find_package(OpenMP REQUIRED)

set(src picopng/picopng.cpp
        stippler/VoronoiDiagramGenerator.cpp
        stippler/bitmap.cpp
        stippler/stippler.cpp
        stippler/stippler_api.cpp
        voronoi/parse_arguments.cpp
        voronoi/voronoi.cpp)

add_executable(voronoi ${src})
target_include_directories(voronoi PRIVATE picopng stippler voronoi)
target_link_libraries(voronoi PRIVATE Boost::program_options
                                      OpenMP::OpenMP_CXX)
