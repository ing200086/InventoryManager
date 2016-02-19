cmake_minimum_required(VERSION 3.1.0)
project (UT_Example C CXX)

file(GLOB SRCS ${TEST_MAIN_DIR}/main.cpp
    ${PROJECT_SOURCE_DIR}/*.h
    ${PROJECT_SOURCE_DIR}/*.cpp
)

ADD_EXECUTABLE(${PROJECT_NAME} ${SRCS})

TARGET_LINK_LIBRARIES(${PROJECT_NAME}
    # TokenLexical
    libgtest
    libgmock
)

target_include_directories(${PROJECT_NAME} PUBLIC
    ${PROJECT_SOURCE_DIR}/include)

add_test(NAME ${PROJECT_NAME}
    COMMAND ${PROJECT_NAME})