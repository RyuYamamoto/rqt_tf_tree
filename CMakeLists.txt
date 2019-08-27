cmake_minimum_required(VERSION 3.5)
project(rqt_tf_tree)
# Load catkin and all dependencies required for this package
#find_package(catkin REQUIRED)
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
#catkin_package()
#catkin_python_setup()
ament_python_install_package(${PROJECT_NAME} PACKAGE_DIR src/${PROJECT_NAME})

install(FILES plugin.xml
#  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  DESTINATION share/${PROJECT_NAME}
)

install(DIRECTORY resource
  #DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  DESTINATION share/${PROJECT_NAME}
)

install(PROGRAMS scripts/rqt_tf_tree
  #DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
  DESTINATION lib/${PROJECT_NAME}
)

if (CATKIN_ENABLE_TESTING)
  catkin_add_nosetests(test/dotcode_tf_test.py
     DEPENDENCIES ${${PROJECT_NAME}_EXPORTED_TARGETS})
endif()

ament_package()