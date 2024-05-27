cmake_minimum_required(VERSION 3.10)

project(MyProject VERSION 1.0)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_library(mylib src/mylib/mylib.cpp)

add_executable(MyProject src/main.cpp)

target_link_libraries(MyProject PRIVATE mylib)

target_include_directories(MyProject PRIVATE ${CMAKE_SOURCE_DIR}/include)

install(TARGETS MyProject DESTINATION bin)
install(TARGETS mylib DESTINATION lib)
install(FILES src/mylib/mylib.h DESTINATION include/mylib)


set(CPACK_PACKAGE_NAME "MyProject")
set(CPACK_PACKAGE_VERSION "1.0")
set(CPACK_PACKAGE_CONTACT "angelusvincent@gmail.com")

set(CPACK_GENERATOR "ZIP")

set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Angelus Vincent")
set(CPACK_DEBIAN_PACKAGE_DEPENDS "c++20")

include(CPack)

