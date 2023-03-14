cmake_minimum_required(VERSION 3.24)
project(chat)

set(CMAKE_CXX_STANDARD 14)

find_package(Boost COMPONENTS thread system REQUIRED)

set(CMAKE_THREAD_PREFER_PTHREAD TRUE)
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)


include_directories(${Boost_INCLUDE_DIRS})

add_executable(chat_client protocol.hpp chat_client.cpp)
add_executable(chat_server protocol.hpp chat_server.cpp)
target_link_libraries(chat_server ${Boost_LIBRARIES} ${CMAKE_THREAD_LIBS_INIT})