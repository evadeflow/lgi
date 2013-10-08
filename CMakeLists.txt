# Copyright (C) 2007-2012 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project (lgi C)
cmake_minimum_required(VERSION 2.8)
include (cmake/dist.cmake)
include (lua)

# Find gobject-instrospection
find_package(PkgConfig REQUIRED)
pkg_check_modules(GOBJECT_INTROSPECTION REQUIRED gobject-introspection-1.0)
include_directories(GOBJECT_INTROSPECTION_INCLUDE_DIRS)

set(
  LGI_SRCS
    lgi/buffer.c
    lgi/callable.c
    lgi/core.c
    lgi/gi.c
    lgi/marshal.c
    lgi/object.c
    lgi/record.c
)
# Create lsqlite module
install_lua_module (lgi ${LGI_SRCS} LINK ${GOBJECT_INTROSPECTION_LIBRARIES})
#install_data (HISTORY README)
#install_doc(doc/)
#install_test (lunit.lua test.lua tests-sqlite3.lua)
#install_example(examples/)
