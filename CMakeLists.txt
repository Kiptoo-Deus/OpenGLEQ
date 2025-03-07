cmake_minimum_required(VERSION 3.10)
project(OpenGLEQ CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find dependencies
find_package(OpenGL REQUIRED)
find_package(glfw3 CONFIG REQUIRED)
find_package(GLEW REQUIRED)
find_package(PortAudio REQUIRED)
find_package(FFTW3 REQUIRED COMPONENTS double)

# Source files
add_executable(OpenGLEQ
    src/main.cpp
    src/renderer.cpp
    src/audio_processor.cpp
)

# Link libraries
target_link_libraries(OpenGLEQ PRIVATE
    OpenGL::GL
    glfw
    GLEW::GLEW
    ${PORTAUDIO_LIBRARIES}
    ${FFTW3_LIBRARIES}
)

# Include directories
target_include_directories(OpenGLEQ PRIVATE
    ${PORTAUDIO_INCLUDE_DIRS}
    ${FFTW3_INCLUDE_DIRS}
)