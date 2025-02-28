cmake_minimum_required(VERSION 3.0)
project(final_project)

find_package(OpenGL REQUIRED)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}")

add_subdirectory(external)

include_directories(
    external/glfw-3.1.2/include/
    external/glm-0.9.7.1/
    external/glad-opengl-3.3/include/
    external/tinygltf-2.9.3/
    final_project/
)

add_executable(final_project
    final_project/final_project.cpp
    final_project/render/shader.cpp
        final_project/view_points/camera/camera.cpp
        final_project/3D_objects/Cube/Cube.cpp
        final_project/3D_objects/skybox/SkyBox.cpp
        final_project/utils/texture_utils.cpp
        final_project/3D_objects/gltf_object/GltfObject.cpp
        final_project/view_points/lights/light/Light.cpp
    final_project/tinygltf_implementation.cpp
        final_project/3D_objects/graphics_object/GraphicsObject.h
        final_project/3D_objects/graphics_object/GraphicsObject.cpp
        final_project/passes/geometry_pass/GeometryPass.cpp
        final_project/passes/geometry_pass/GeometryPass.h
        final_project/passes/render_pass/RenderPass.cpp
        final_project/passes/render_pass/RenderPass.h
        final_project/passes/ssao_pass/SSAOPass.cpp
        final_project/passes/ssao_pass/SSAOPass.h
        final_project/utils/renderQuad.cpp
        final_project/utils/renderQuad.h
        final_project/passes/ssao_blur_pass/SSAOBlurPass.cpp
        final_project/passes/ssao_blur_pass/SSAOBlurPass.h
        final_project/passes/lighting_pass/LightingPass.cpp
        final_project/passes/lighting_pass/LightingPass.h
        final_project/passes/depth_pass/DepthPass.cpp
        final_project/passes/depth_pass/DepthPass.h
        final_project/view_points/lights/spot_light/Spotlight.cpp
        final_project/view_points/lights/spot_light/Spotlight.h
        final_project/view_points/lights/LightTypes.h
        final_project/view_points/view_point/ViewPoint.cpp
        final_project/view_points/view_point/ViewPoint.h
)

target_link_libraries(final_project
    ${OPENGL_LIBRARY}
    glfw
    glad
)

