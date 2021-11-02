cmake_minimum_required(VERSION 3.2)

PROJECT(dmidecode)

LIST(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
INCLUDE(cmake/ModuleImport.cmake)
INCLUDE(cmake/ModuleCompileOptions.cmake)
ModuleSetCompileOptions()
ModuleSetWinCompilerFlags()

SET(DMIDECODE_VERSION_MAJOR "1")
SET(DMIDECODE_VERSION_MINOR "0")
SET(DMIDECODE_VERSION_PATCH "1")
SET(DMIDECODE_VERSION "${DMIDECODE_VERSION_MAJOR}.${DMIDECODE_VERSION_MINOR}.${DMIDECODE_VERSION_PATCH}")

MESSAGE(STATUS "VERSION: ${DMIDECODE_VERSION}")

OPTION(USE_DMIDECODE "use dmidecode" OFF)

LibImport("libdmidecode" "src/libdmidecode")
ExeImport("tools" "libdmidecode")

#ADD_CUSTOM_COMMAND(
#TARGET dmidecodetest
#PRE_BUILD
#COMMAND ${CMAKE_COMMAND} -E copy_if_different
#${CMAKE_CURRENT_SOURCE_DIR}/config/test.csv
#$<TARGET_FILE_DIR:dmidecodetest>
#)

#INSTALL(DIRECTORY include/ DESTINATION include)
#INSTALL(TARGETS dmidecode
#        RUNTIME DESTINATION bin
#        LIBRARY DESTINATION lib
#        ARCHIVE DESTINATION lib)

#SET(DMIDECODE_LIBS "dmidecode")
#MARK_AS_ADVANCED(${DMIDECODE_LIBS})