cmake_minimum_required(VERSION 3.2)

option(HUNTER_STATUS_DEBUG "..." ON)
set(HUNTER_ROOT "${CMAKE_CURRENT_LIST_DIR}/__HUNTER" CACHE PATH "...")

include("cmake/HunterGate.cmake")

HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.151.tar.gz"
    SHA1 "68657b81508c2d3c248731b5a0c2125f19866721"
)

project(foo)

hunter_add_package(${PKG})
