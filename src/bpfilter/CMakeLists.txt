# SPDX-License-Identifier: GPL-2.0-only
# Copyright (c) 2023 Meta Platforms, Inc. and affiliates.

add_executable(bpfilter
    ${CMAKE_CURRENT_SOURCE_DIR}/main.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/cgen.h              ${CMAKE_CURRENT_SOURCE_DIR}/cgen/cgen.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/dump.h              ${CMAKE_CURRENT_SOURCE_DIR}/cgen/dump.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/fixup.h             ${CMAKE_CURRENT_SOURCE_DIR}/cgen/fixup.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/jmp.h               ${CMAKE_CURRENT_SOURCE_DIR}/cgen/jmp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/ip4.h       ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/ip4.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/ip6.h       ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/ip6.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/tcp.h       ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/tcp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/udp.h       ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/udp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/meta.h      ${CMAKE_CURRENT_SOURCE_DIR}/cgen/matcher/meta.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/nf.h                ${CMAKE_CURRENT_SOURCE_DIR}/cgen/nf.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/printer.h           ${CMAKE_CURRENT_SOURCE_DIR}/cgen/printer.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/program.h           ${CMAKE_CURRENT_SOURCE_DIR}/cgen/program.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/prog/map.h          ${CMAKE_CURRENT_SOURCE_DIR}/cgen/prog/map.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/reg.h
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/stub.h              ${CMAKE_CURRENT_SOURCE_DIR}/cgen/stub.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/swich.h             ${CMAKE_CURRENT_SOURCE_DIR}/cgen/swich.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/tc.h                ${CMAKE_CURRENT_SOURCE_DIR}/cgen/tc.c
    ${CMAKE_CURRENT_SOURCE_DIR}/cgen/xdp.h               ${CMAKE_CURRENT_SOURCE_DIR}/cgen/xdp.c
    ${CMAKE_CURRENT_SOURCE_DIR}/context.h                ${CMAKE_CURRENT_SOURCE_DIR}/context.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/cli.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/front.h            ${CMAKE_CURRENT_SOURCE_DIR}/xlate/front.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/ipt/dump.h         ${CMAKE_CURRENT_SOURCE_DIR}/xlate/ipt/dump.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/ipt/helpers.h
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/ipt/ipt.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/nft/nfgroup.h      ${CMAKE_CURRENT_SOURCE_DIR}/xlate/nft/nfgroup.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/nft/nfmsg.h        ${CMAKE_CURRENT_SOURCE_DIR}/xlate/nft/nfmsg.c
    ${CMAKE_CURRENT_SOURCE_DIR}/xlate/nft/nft.c
)

target_include_directories(bpfilter
    PUBLIC
        ${CMAKE_SOURCE_DIR}/src
)

target_link_libraries(bpfilter
    PRIVATE
        bf_global_flags
        core
        PkgConfig::nl
)
