#   BSD LICENSE
#
#   Copyright(c) 2010-2015 Intel Corporation. All rights reserved.
#   All rights reserved.
#
#   Redistribution and use in source and binary forms, with or without
#   modification, are permitted provided that the following conditions
#   are met:
#
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above copyright
#       notice, this list of conditions and the following disclaimer in
#       the documentation and/or other materials provided with the
#       distribution.
#     * Neither the name of Intel Corporation nor the names of its
#       contributors may be used to endorse or promote products derived
#       from this software without specific prior written permission.
#
#   THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#   "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
#   LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
#   A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
#   OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
#   SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
#   LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
#   DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
#   THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
#   (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
#   OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

include $(RTE_SDK)/mk/rte.vars.mk

ifeq ($(CONFIG_RTE_TEST_PMD),y)

#
# library name
#
APP = testpmd

CFLAGS += -O3
CFLAGS += $(WERROR_FLAGS)

#
# all source are stored in SRCS-y
#
SRCS-y := testpmd.c
SRCS-y += parameters.c
SRCS-$(CONFIG_RTE_LIBRTE_CMDLINE) += cmdline.c
SRCS-$(CONFIG_RTE_LIBRTE_CMDLINE) += cmdline_flow.c
SRCS-y += config.c
SRCS-y += iofwd.c
SRCS-y += macfwd.c
SRCS-y += macswap.c
SRCS-y += flowgen.c
SRCS-y += rxonly.c
SRCS-y += txonly.c
SRCS-y += s-txonly.c
SRCS-y += csumonly.c
SRCS-y += icmpecho.c
SRCS-$(CONFIG_RTE_LIBRTE_IEEE1588) += ieee1588fwd.c

ifeq ($(CONFIG_RTE_BUILD_SHARED_LIB),y)

ifeq ($(CONFIG_RTE_LIBRTE_PMD_BOND),y)
LDLIBS += -lrte_pmd_bond
endif

ifeq ($(CONFIG_RTE_LIBRTE_IXGBE_PMD),y)
LDLIBS += -lrte_pmd_ixgbe
endif

ifeq ($(CONFIG_RTE_LIBRTE_I40E_PMD),y)
LDLIBS += -lrte_pmd_i40e
endif

ifeq ($(CONFIG_RTE_LIBRTE_PMD_XENVIRT),y)
LDLIBS += -lrte_pmd_xenvirt
endif

endif

CFLAGS_cmdline.o := -D_GNU_SOURCE

include $(RTE_SDK)/mk/rte.app.mk

endif
