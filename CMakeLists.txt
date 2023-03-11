cmake_minimum_required(VERSION 3.24)

project(
	CraftingCategories
	VERSION 1.0.1
	LANGUAGES CXX
)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

list(APPEND CMAKE_IGNORE_PATH "${PROJECT_BINARY_DIR}")
list(APPEND CMAKE_MODULE_PATH
	"${PROJECT_SOURCE_DIR}/tools/Modules"
)
include(SKSEPlugin)

SKSEPlugin_Add(
	${PROJECT_NAME}
	SOURCE_DIR src
	SOURCES
		.clang-format
		.editorconfig
		README.md
		vcpkg.json
	PRECOMPILE_HEADERS
		src/PCH/PCH.h
)

find_package(jsoncpp CONFIG REQUIRED)
find_package(tsl-ordered-map CONFIG REQUIRED)

target_link_libraries(
	${PROJECT_NAME}
	PRIVATE
		jsoncpp_static
		tsl::ordered_map
)
