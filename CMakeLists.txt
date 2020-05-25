cmake_minimum_required(VERSION 3.11.3)

set(CMAKE_CXX_STANDARD 17)

project(Membot)

find_package(wxWidgets REQUIRED COMPONENTS core base)
include(${wxWidgets_USE_FILE})

file(GLOB project_SRCS src/*.cpp)
file(GLOB project_HEADERS src/*.h)


add_custom_target(
        clangformat
        COMMAND /usr/bin/clang-format
        -style=Google
        -i
        ${project_SRCS}
        ${project_HEADERS}
)

add_executable(membot ${project_SRCS})
target_link_libraries(membot ${wxWidgets_LIBRARIES})
target_include_directories(membot PRIVATE ${wxWidgets_INCLUDE_DIRS})
