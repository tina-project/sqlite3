project(sqlite3 VERSION 3.45.3 LANGUAGES C)

set(SQLITE3_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include" CACHE INTERNAL "${CMAKE_CURRENT_SOURCE_DIR}/include")

add_library(sqlite3 SHARED
    ${CMAKE_CURRENT_SOURCE_DIR}/src/sqlite3.c
)
if(UNIX)
    target_link_libraries(sqlite3
        dl
    )
endif()
set_target_properties(sqlite3 PROPERTIES
    OUTPUT_NAME sqlite3
    VERSION ${PROJECT_VERSION}
    SOVERSION 3
    POSITION_INDEPENDENT_CODE ON
)
