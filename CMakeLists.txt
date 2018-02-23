cmake_minimum_required(VERSION 3.2)

project(liquibook LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 11)

set (HEADERS
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/trade_listener.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/logger.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/order_book_listener.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/order_listener.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/depth_constants.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/bbo_listener.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/order.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/types.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/callback.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/comparable_price.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/depth.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/depth_order_book.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/version.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/depth_level.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/order_book.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/depth_listener.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/book/order_tracker.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/simple/simple_order_book.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/simple/simple_order.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/liquibook_export.h
    )

add_library(liquibook INTERFACE)
add_library(OCI::liquibook ALIAS liquibook)

add_subdirectory(quickfast)

find_package(Boost MODULE REQUIRED)

target_sources(liquibook INTERFACE ${HEADERS})
target_include_directories(liquibook
    INTERFACE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
        ${Boost_INCLUDE_DIRS}
    )
target_link_libraries(liquibook
    INTERFACE
        OCI::quickfast
    )


add_subdirectory(examples)
