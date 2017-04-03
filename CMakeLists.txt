cmake_minimum_required (VERSION 2.6 FATAL_ERROR)
project      (pointcloudserver)
set (CMAKE_PREFIX_PATH "D:\\Qt\\Qt5.6.0\\5.6\\msvc2013_64;D:\\pcl-master")
find_package (VTK 6.3.0 REQUIRED)
find_package (PCL 1.8 REQUIRED)
find_package(CUDA)
include("./cmake/find_cuda.cmake")
include_directories (${PCL_INCLUDE_DIRS})
link_directories    (${PCL_LIBRARY_DIRS})
add_definitions     (${PCL_DEFINITIONS})

set  (CMAKE_AUTORCC ON)
set  (project_SOURCES main.cpp)
set  (project_HEADERS )
set  (project_FORMS   )
set  (project_RESOURCES Resources/Resources.qrc)
#set  (CMAKE_CXX_FLAGS -g)
set(CMAKE_CXX_STANDARD 11)


QT5_WRAP_CPP (project_HEADERS_MOC   ${project_HEADERS})
QT5_WRAP_UI  (project_FORMS_HEADERS ${project_FORMS})
QT5_ADD_RESOURCES(project_RESOURCES_RCC ${project_RESOURCES})

ADD_DEFINITIONS (${QT_DEFINITIONS})


ADD_EXECUTABLE  (pointcloudserver ${project_SOURCES}
                                  ${project_FORMS_HEADERS}
				  ${project_RESOURCES} ${project_HEADERS_MOC})
																				
																				TARGET_LINK_LIBRARIES (pointcloudserver ${PCL_LIBRARIES})
																				qt5_use_modules (pointcloudserver Widgets)

