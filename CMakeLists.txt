cmake_minimum_required(VERSION 3.25)

include(cmake/rho-boot.cmake)
project(beicode
	VERSION 1.0.0
	DESCRIPTION "A simple utf-8 based unicode decoding and encoding library"
	HOMEPAGE_URL "https://github.com/northwindtraders/beicode"
	LANGUAGES CXX)

rho_add_library(beicode
	SKIP_COMMON_FLAGS)

target_compile_features(beicode PUBLIC cxx_std_17)
