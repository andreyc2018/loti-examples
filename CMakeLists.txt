cmake_minimum_required(VERSION 3.15)
project(liburing_examples C)

set(CMAKE_C_STANDARD 99)

find_package(PkgConfig REQUIRED)
pkg_check_modules(URING REQUIRED liburing)

find_package(Threads REQUIRED)

add_executable(probe probe.c)
target_link_libraries(probe ${URING_LINK_LIBRARIES})
target_include_directories(probe PUBLIC ${URING_INCLUDE_DIRS})

add_executable(link link.c)
target_link_libraries(link ${URING_LINK_LIBRARIES})
target_include_directories(link PUBLIC ${URING_INCLUDE_DIRS})

add_executable(fixed_buffers fixed_buffers.c)
target_link_libraries(fixed_buffers ${URING_LINK_LIBRARIES})
target_include_directories(fixed_buffers PUBLIC ${URING_INCLUDE_DIRS})

add_executable(sq_poll sq_poll.c)
target_link_libraries(sq_poll ${URING_LINK_LIBRARIES})
target_include_directories(sq_poll PUBLIC ${URING_INCLUDE_DIRS})

add_executable(provide_buffers provide_buffers.c)
target_link_libraries(provide_buffers ${URING_LINK_LIBRARIES})
target_include_directories(provide_buffers PUBLIC ${URING_INCLUDE_DIRS})

add_executable(eventfd eventfd.c)
target_link_libraries(eventfd ${URING_LINK_LIBRARIES} Threads::Threads)
target_include_directories(eventfd PUBLIC ${URING_INCLUDE_DIRS})

add_executable(cat_io_uring cat_io_uring.c)

add_executable(cat_liburing cat_liburing.c)
target_link_libraries(cat_liburing ${URING_LINK_LIBRARIES})
target_include_directories(cat_liburing PUBLIC ${URING_INCLUDE_DIRS})

add_executable(cp_liburing cp_liburing.c)
target_link_libraries(cp_liburing ${URING_LINK_LIBRARIES})
target_include_directories(cp_liburing PUBLIC ${URING_INCLUDE_DIRS})

add_executable(webserver_liburing webserver_liburing.c)
target_link_libraries(webserver_liburing ${URING_LINK_LIBRARIES})
target_include_directories(webserver_liburing PUBLIC ${URING_INCLUDE_DIRS})
