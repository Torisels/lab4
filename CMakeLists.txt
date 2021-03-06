cmake_minimum_required(VERSION 2.8.4)
project(cpp)

# CMake FindThreads is broken until 3.1
#find_package(Threads REQUIRED)
set(CMAKE_THREAD_LIBS_INIT pthread)

set(CMAKE_CXX_STANDARD 17)


set(EXT_PROJECTS_DIR ${PROJECT_SOURCE_DIR}/ext)
set(gtest_SOURCE_DIR ${EXT_PROJECTS_DIR}/googletest/googletest)


enable_testing()
include_directories(${gtest_SOURCE_DIR}/include)


set(FROST_FRUIT_SOURCE_FILES
        Frostfruit.cc
        Frostfruit.h
		#IItem.h
        #NormalItem.h
        #CheeseItem.h
        #LegolasItem.h
        #ConcertTicketItem.h
        )

set(FROST_FRUIT_UNIT_TESTS_SOURCE_FILES
        ${FROST_FRUIT_SOURCE_FILES}
        FrostfruitUnitTests.cc)

#set(SOURCE_FILES
#        ${FROST_FRUIT_SOURCE_FILES}
#        ${FROST_FRUIT_TEXT_TESTS_SOURCE_FILES})

add_subdirectory(${gtest_SOURCE_DIR} ${gtest_SOURCE_DIR}/bin EXCLUDE_FROM_ALL)
add_executable(Frostfruit ${FROST_FRUIT_SOURCE_FILES} FrostfruitMain.cc)

#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
#target_link_libraries(Frostfruit gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})

add_executable(FrostfruitUnitTests ${FROST_FRUIT_UNIT_TESTS_SOURCE_FILES})
target_link_libraries(FrostfruitUnitTests gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})



#set(FROST_FRUIT_CHARACTERIZATION_TESTS_SOURCE_FILES
#        ${FROST_FRUIT_SOURCE_FILES}
#        FrostfruitCharacterizationTests.cc)

#set(SOURCE_FILES
#        ${ABC_SOURCE_FILES}
#        ${CDE_TEXT_TESTS_SOURCE_FILES})



#add_executable(FrostfruitCharacterizationTests ${FROST_FRUIT_CHARACTERIZATION_TESTS_SOURCE_FILES})
#target_link_libraries(FrostfruitCharacterizationTests gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
