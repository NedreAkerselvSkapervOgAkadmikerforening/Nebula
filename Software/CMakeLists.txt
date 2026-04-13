cmake_minimum_required(VERSION 3.13)
project("wawa")

# === Gather wawa sources === 
file(GLOB_RECURSE wawa_SOURCES CONFIGURE_DEPENDS
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp"
)

# === Create the wawa library ===
add_executable(wawa ${wawa_SOURCES})

# Include directories
target_include_directories(wawa PUBLIC
    src
)
