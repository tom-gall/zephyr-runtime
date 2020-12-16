# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.13.1)
set(ENV{QEMU_BIN_PATH} "${CMAKE_SOURCE_DIR}/qemu-hack")

set(QEMU_PIPE "\${QEMU_PIPE}")  # QEMU_PIPE is set by the calling TVM instance.

find_package(Zephyr HINTS $ENV{ZEPHYR_BASE})
project(microtvm_zephyr_runtime)

set(CMAKE_VERBOSE_MAKEFILE ON)
file(GLOB TVM_SOURCES ${CMAKE_SOURCE_DIR}/__tvm*.c)
target_sources(app PRIVATE src/main.c ${TVM_SOURCES})

target_link_libraries(app
  PRIVATE
  ${CMAKE_CURRENT_LIST_DIR}/libtvm__libutvm_rpc_server.a 
  ${CMAKE_CURRENT_LIST_DIR}/libtvm__libutvm_rpc_common.a 
  ${CMAKE_CURRENT_LIST_DIR}/libtvm__libcommon.a 
  ${CMAKE_CURRENT_LIST_DIR}/libtvm__libmodule.a
  ${CMAKE_CURRENT_LIST_DIR}/libtvm__libsrc.a
)

target_include_directories(app 
  PRIVATE
  "${CMAKE_CURRENT_LIST_DIR}/../tvm/include"
  "${CMAKE_CURRENT_LIST_DIR}/crt"
)
