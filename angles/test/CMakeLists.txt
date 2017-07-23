if (BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
	
  ament_add_gtest(${PROJECT_NAME}_utest utest.cpp)
  ament_add_nose_test(${PROJECT_NAME}_nose_test utest.py)
endif(BUILD_TESTING)
