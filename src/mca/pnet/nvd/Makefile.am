# -*- makefile -*-
#
# Copyright (c) 2004-2005 The Trustees of Indiana University and Indiana
#                         University Research and Technology
#                         Corporation.  All rights reserved.
# Copyright (c) 2004-2005 The University of Tennessee and The University
#                         of Tennessee Research Foundation.  All rights
#                         reserved.
# Copyright (c) 2004-2005 High Performance Computing Center Stuttgart,
#                         University of Stuttgart.  All rights reserved.
# Copyright (c) 2004-2005 The Regents of the University of California.
#                         All rights reserved.
# Copyright (c) 2012      Los Alamos National Security, Inc.  All rights reserved.
# Copyright (c) 2013-2019 Intel, Inc.  All rights reserved.
# Copyright (c) 2017      Research Organization for Information Science
#                         and Technology (RIST). All rights reserved.
# Copyright (c) 2021      Nanook Consulting.  All rights reserved.
# $COPYRIGHT$
#
# Additional copyrights may follow
#
# $HEADER$
#

AM_CPPFLAGS = $(pnet_nvd_CPPFLAGS)

headers = pnet_nvd.h
sources = \
        pnet_nvd_component.c \
        pnet_nvd.c

# Make the output library in this directory, and name it either
# mca_<type>_<name>.la (for DSO builds) or libmca_<type>_<name>.la
# (for static builds).

if MCA_BUILD_pmix_pnet_nvd_DSO
lib =
lib_sources =
component = mca_pnet_nvd.la
component_sources = $(headers) $(sources)
else
lib = libmca_pnet_nvd.la
lib_sources = $(headers) $(sources)
component =
component_sources =
endif

mcacomponentdir = $(pmixlibdir)
mcacomponent_LTLIBRARIES = $(component)
mca_pnet_nvd_la_SOURCES = $(component_sources)
mca_pnet_nvd_la_LIBADD = $(pnet_nvd_LIBS)
mca_pnet_nvd_la_LDFLAGS = -module -avoid-version $(pnet_nvd_LDFLAGS)
if NEED_LIBPMIX
mca_pnet_nvd_la_LIBADD += $(top_builddir)/src/libpmix.la
endif

noinst_LTLIBRARIES = $(lib)
libmca_pnet_nvd_la_SOURCES = $(lib_sources)
libmca_pnet_nvd_la_LIBADD = $(pnet_nvd_LIBS)
libmca_pnet_nvd_la_LDFLAGS = -module -avoid-version $(pnet_nvd_LDFLAGS)
