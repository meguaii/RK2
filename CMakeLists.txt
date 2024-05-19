cmake_minimum_required(VERSION 3.10)
project(SimpleFactory)

set(CMAKE_CXX_STANDARD 17)

include_directories(.)

# Создание исполняемого файла SimpleFactory
add_executable(SimpleFactory main.cpp SimpleFactory.cpp)

# Включение поддержки тестирования
enable_testing()

# Добавление Google Test
add_subdirectory(lib/googletest)
include_directories(lib/googletest/googletest/include)

# Создание исполняемого файла для тестов
add_executable(SimpleFactoryTests test/SimpleFactoryTest.cpp SimpleFactory.cpp)

# Линковка с Google Test
target_link_libraries(SimpleFactoryTests gtest)

# Добавление теста
add_test(NAME SimpleFactoryTests COMMAND SimpleFactoryTests)
