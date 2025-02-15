add_subdirectory(kernel)

add_library(tgeometry OBJECT $<TARGET_OBJECTS:tgeometry_kernel>)

target_sources(tgeometry PRIVATE
    Image.cpp
    PointCloud.cpp
    RaycastingScene.cpp
    RGBDImage.cpp
    TensorMap.cpp
    TriangleMesh.cpp
    TSDFVoxelGrid.cpp
)

open3d_show_and_abort_on_warning(tgeometry)
open3d_set_global_properties(tgeometry)
open3d_set_open3d_lib_properties(tgeometry)
open3d_link_3rdparty_libraries(tgeometry)

if(BUILD_CUDA_MODULE)
    target_include_directories(tgeometry SYSTEM PRIVATE
        ${CMAKE_CUDA_TOOLKIT_INCLUDE_DIRECTORIES})
endif()
