cmake_minimum_required(VERSION 3.16)
project(VideoEditor VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

# Set Qt6 path
set(QT_DIR "C:/Qt/6.9.0/msvc2022_64/lib/cmake/Qt6")
if(EXISTS ${QT_DIR})
    list(APPEND CMAKE_PREFIX_PATH ${QT_DIR})
else()
    message(WARNING "Qt6 directory not found at ${QT_DIR}. Please set the correct path to your Qt6 installation.")
endif()

# Find Qt6 Widgets
find_package(Qt6 COMPONENTS Widgets REQUIRED)

# Make the executable
add_executable(VideoEditor
    src/main.cpp
)

# Link to Qt libraries
target_link_libraries(VideoEditor
    Qt6::Widgets
)

# Set output directories
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

# Install rules
install(TARGETS VideoEditor
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)

# Copy Qt dependencies to output directory
if(WIN32)
    add_custom_command(TARGET VideoEditor POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_if_different
            $<TARGET_FILE:Qt6::Core>
            $<TARGET_FILE:Qt6::Widgets>
            $<TARGET_FILE_DIR:VideoEditor>
    )
endif()
