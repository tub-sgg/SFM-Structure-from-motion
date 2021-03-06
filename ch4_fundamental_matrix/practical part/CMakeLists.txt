cmake_minimum_required(VERSION 3.1)

project( pcv3 LANGUAGES CXX )

find_package( OpenCV REQUIRED )




add_library(code 
    Pcv4.cpp
    Pcv4.h
    Helper.cpp
    Helper.h
)

set_target_properties(code PROPERTIES
    CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
)

target_link_libraries(code 
    PUBLIC
        opencv_core opencv_highgui opencv_imgproc opencv_calib3d
)




add_executable(main_manual
    main_manual.cpp 
)

target_link_libraries(main_manual 
    PRIVATE
        code
)


add_executable(main_automatic
    main_automatic.cpp 
)

target_link_libraries(main_automatic 
    PRIVATE
        code
)


add_executable(unit_test 
    unit_test.cpp 
)

target_link_libraries(unit_test 
    PRIVATE
        code
)
