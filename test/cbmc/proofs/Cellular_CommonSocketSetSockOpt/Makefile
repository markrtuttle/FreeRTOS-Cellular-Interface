#
# Copyright (C) 2020 Amazon.com, Inc. or its affiliates.  All Rights Reserved.
#
# Permission is hereby granted, free of charge, to any person obtaining a copy of
# this software and associated documentation files (the "Software"), to deal in
# the Software without restriction, including without limitation the rights to
# use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
# the Software, and to permit persons to whom the Software is furnished to do so,
# subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
# FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
# COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
# IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
# CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
#


HARNESS_ENTRY=harness
HARNESS_FILE=Cellular_CommonSocketSetSockOpt_harness
PROOF_UID = Cellular_CommonSocketSetSockOpt

DEFINES +=
INCLUDES +=

REMOVE_FUNCTION_BODY += _Cellular_TranslatePktStatus
REMOVE_FUNCTION_BODY += _Cellular_CheckLibraryStatus

# This value was experimentally chosen to provide 100% coverage
# without tripping unwinding assertions and without exhausting memory.
CBMC_MAX_BUFSIZE=13

UNWINDSET += __CPROVER_file_local_cellular_common_c__Cellular_FreeContext.0:$(CBMC_MAX_BUFSIZE)
UNWINDSET += _Cellular_CreateSocketData.0:$(CBMC_MAX_BUFSIZE)
UNWINDSET += harness.0:$(CBMC_MAX_BUFSIZE)

PROOF_SOURCES += $(PROOFDIR)/$(HARNESS_FILE).c
PROOF_SOURCES += $(SRCDIR)/test/cbmc/sources/cellular_cbmc_state.c
PROOF_SOURCES += $(SRCDIR)/test/cbmc/sources/global_state_cellular.c
PROJECT_SOURCES += $(SRCDIR)/source/cellular_common_api.c
PROJECT_SOURCES += $(SRCDIR)/source/cellular_common.c

include ../Makefile.common
