cmake_minimum_required(VERSION 3.11)
project(Meshes)

add_executable(cube cube.cpp)
add_executable(circle circle.cpp)
add_executable(tor tor.cpp)
add_executable(eevee Eevee.cpp)

add_library(gmsh SHARED IMPORTED)
set_target_properties(gmsh PROPERTIES
    IMPORTED_LOCATION "/usr/lib/x86_64-linux-gnu/libgmsh.so"
    INTERFACE_INCLUDE_DIRECTORIES "/usr/include"
)
set(GMSH_LIBRARIES gmsh)


target_link_libraries(cube ${GMSH_LIBRARIES})
target_link_libraries(circle ${GMSH_LIBRARIES})
target_link_libraries(tor ${GMSH_LIBRARIES})
target_link_libraries(eevee ${GMSH_LIBRARIES})


