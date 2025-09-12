cmake_minimum_required(VERSION 3.25)

set(beicode_VERSION 1.0.0)

include(cmake/rho-boot.cmake)
project(beicode
	VERSION ${beicode_VERSION}
	DESCRIPTION "A simple utf-8 based unicode decoding and encoding library"
	HOMEPAGE_URL "https://github.com/northwindtraders/beicode"
	LANGUAGES CXX)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

rho_add_library(beicode
	SKIP_COMMON_FLAGS
	SKIP_INSTALL)

target_compile_features(beicode PUBLIC cxx_std_17)

configure_package_config_file(cmake/config.cmake.in
	${CMAKE_CURRENT_BINARY_DIR}/beicode-config.cmake
	INSTALL_DESTINATION ${CMAKE_INSTALL_DATADIR}/beicode
	NO_SET_AND_CHECK_MACRO)
write_basic_package_version_file(
	${CMAKE_CURRENT_BINARY_DIR}/beicode-config-version.cmake
	VERSION ${beicode_VERSION}
	COMPATIBILITY SameMajorVersion)
install(
	FILES
		${CMAKE_CURRENT_BINARY_DIR}/beicode-config.cmake
		${CMAKE_CURRENT_BINARY_DIR}/beicode-config-version.cmake
	DESTINATION
		${CMAKE_INSTALL_DATADIR}/beicode)

install(TARGETS beicode
	EXPORT beicode-targets
	FILE_SET HEADERS)
install(DIRECTORY include/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(EXPORT beicode-targets
	NAMESPACE beicode::
	DESTINATION ${CMAKE_INSTALL_DATADIR}/beicode)
