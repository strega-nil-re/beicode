cmake_minimum_required(VERSION 3.25)

include(cmake/rho-boot.cmake)
project(beicode
	VERSION 1.0.0
	DESCRIPTION "A simple utf-8 based unicode decoding and encoding library"
	HOMEPAGE_URL "https://github.com/northwindtraders/beicode"
	LANGUAGES CXX)

set(RHO_DISABLED_GNU_WARNING_FLAGS sign-conversion)

set(RHO_CXX_STANDARD 17)
rho_add_library(beicode)
