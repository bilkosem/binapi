

set(BINAPI_HEADERS
    binapi/api.hpp
    binapi/flatjson.hpp
    binapi/dtf.hpp
    binapi/double_type.hpp
    binapi/enums.hpp
    binapi/errors.hpp
    binapi/invoker.hpp
    binapi/message.hpp
    binapi/pairslist.hpp
    binapi/reports.hpp
    binapi/tools.hpp
    binapi/types.hpp
    binapi/websocket.hpp
)

set(BINAPI_SOURCES
    src/api.cpp
    src/enums.cpp
    src/errors.cpp
    src/pairslist.cpp
    src/reports.cpp
    src/tools.cpp
    src/types.cpp
    src/websocket.cpp
)


project(binapi)


if (DEFINED ${BOOST_INCLUDE_DIR})
    include_directories(
        ${BOOST_INCLUDE_DIR}
    )
endif()

add_library(binapi STATIC ${BINAPI_SOURCES})
target_include_directories(binapi PUBLIC ${CMAKE_CURRENT_LIST_DIR}/include)

if (DEFINED ${BOOST_LIB_DIR})
    target_link_libraries(
        ${PROJECT_NAME}
        -L${BOOST_LIB_DIR}
    )
endif()

target_link_libraries(
    ${PROJECT_NAME}
    z
    crypto
    ssl
    pthread
)

# Include header files

# Create shared library


# Install library
#install(TARGETS ${PROJECT_NAME} DESTINATION lib/${PROJECT_NAME})

# Install library headers
#install(FILES ${BINAPI_HEADERS} DESTINATION include/${PROJECT_NAME})