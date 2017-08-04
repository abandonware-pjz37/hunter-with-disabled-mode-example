cmake_minimum_required(VERSION 3.4) # OpenSSL::SSL

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.19.57.tar.gz"
    SHA1 "f83ea762f0609c48a583d0e877a6358f6fbfe0d7"
)

project(foo)

add_executable(foo foo.cpp)

hunter_add_package(CURL)
find_package(CURL CONFIG REQUIRED)
target_link_libraries(foo PUBLIC CURL::libcurl)

hunter_add_package(OpenSSL)
find_package(OpenSSL REQUIRED)
target_link_libraries(foo PUBLIC OpenSSL::SSL OpenSSL::Crypto)
