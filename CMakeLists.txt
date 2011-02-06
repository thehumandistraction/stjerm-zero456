# Minimum cmake version required to build
cmake_minimum_required(VERSION 2.8)

# Define Stjerm's name
project(stjerm)

# Version number
set(stjerm_version 0.15pre)

# This takes the file version.h.in and replaces it with version.h.  This allows
# the version name and number defined above to be used by stjerm.  See the file
# version.h.in for more info.

configure_file("${stjerm_SOURCE_DIR}/version.h.in" "${stjerm_BINARY_DIR}/version.h")

find_package(PkgConfig)
pkg_check_modules(GTK REQUIRED gtk+-2.0>=2.22) 
pkg_check_modules(VTE REQUIRED vte>=0.26)

add_definitions(${GTK_CFLAGS} ${GTK_CFLAGS_OTHER} 
                ${VTE_CFLAGS} ${VTE_CFLAGS_OTHER})

# Note that we add the stjerm_BINARY_DIR in the include_directories section.
# This is necessary so we can pick up version.h once it's created from
# version.h.in.                                                              

include_directories(${GTK_INCLUDE_DIRS}  
                    ${VTE_INCLUDE_DIRS} 
                    ${stjerm_BINARY_DIR})
                    
link_libraries(${GTK_LIBRARIES}  
               ${VTE_LIBRARIES})
               
link_directories(${GTK_LIBRARY_DIRS}  
                 ${VTE_LIBRARY_DIRS})
                
add_subdirectory(src) #Move to the src directory and run the CMakeLists.txt there                 

#INCLUDE(CPack)
#install(TARGETS src/stjerm DESTINATION bin)
