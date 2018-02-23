cmake_minimum_required(VERSION 3.2)

project(depth_feed_publisher)

# EXECUTABLE: Depth Feed Publisher
find_package(Boost MODULE REQUIRED COMPONENTS system thread)
add_executable(depth_feed_publisher
    example_order_book.h
    template_consumer.h
    sleep.h
    exchange.h
    order.h
    asio_safe_include.h
    depth_feed_publisher.h
    depth_feed_connection.h
    depth_feed_connection.cpp
    order.cpp
    template_consumer.cpp
    depth_feed_publisher.cpp
    publisher_main.cpp
    example_order_book.cpp
    exchange.cpp
    )

target_link_libraries(depth_feed_publisher
    PRIVATE
        OCI::liquibook
        Boost::system
        Boost::thread
    )

# EXECUTABLE: Depth Feed Subscriber
add_executable(depth_feed_subscriber
    asio_safe_include.h
    depth_feed_connection.cpp
    depth_feed_connection.h
    depth_feed_publisher.h
    depth_feed_subscriber.cpp
    depth_feed_subscriber.h
    order.cpp
    order.h
    subscriber_main.cpp
    template_consumer.cpp
    )

target_link_libraries(depth_feed_subscriber
    PRIVATE
        OCI::liquibook
        Boost::system
    )
