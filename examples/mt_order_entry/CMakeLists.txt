cmake_minimum_required(VERSION 3.2)

project(mt_order_entry)

add_executable(mt_order_entry
    Order.h
    Market.h
    OrderFwd.h
    Util.h
    Util.cpp
    Order.cpp
    Market.cpp
    mt_order_entry_main.cpp
    )

target_link_libraries(mt_order_entry
    PRIVATE
        OCI::liquibook
    )
