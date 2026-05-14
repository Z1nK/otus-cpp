find_package(GTest QUIET)

if (NOT GTest_FOUND)
	include(FetchContent)
	FetchContent_Declare(
		googletest
		GIT_REPOSITORY https://github.com/google/googletest.git
		GIT_TAG v1.15.2
	)
	FetchContent_MakeAvailable(googletest)
endif()

add_executable(gtest_test_version gtest_test_version.cpp)

set_target_properties(gtest_test_version PROPERTIES
	CXX_STANDARD 14
	CXX_STANDARD_REQUIRED ON
)

target_link_libraries(gtest_test_version PRIVATE
	GTest::gtest
	GTest::gtest_main
	helloworld
)

include(GoogleTest)
gtest_discover_tests(gtest_test_version)
