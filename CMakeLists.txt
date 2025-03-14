cmake_minimum_required(VERSION 3.10)

project(Cpp-y-Bird)

find_package(SDL2 REQUIRED)
find_package(SDL2_image REQUIRED)

set(CMAKE_CXX_STANDARD 17)
# Output of build to bin folder
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

add_executable(Cpp-y-Bird src/main.cpp src/game.cpp src/renderer.cpp src/controller.cpp src/bird.cpp src/pipe.cpp)

# Link SDL2 to your project
target_link_libraries(Cpp-y-Bird SDL2::SDL2 SDL2_image::SDL2_image)

# Copy the assets folder to the bin folder
add_custom_command(TARGET Cpp-y-Bird POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${CMAKE_SOURCE_DIR}/assets $<TARGET_FILE_DIR:Cpp-y-Bird>/assets
)