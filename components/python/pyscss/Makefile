#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2013, 2019, Oracle and/or its affiliates. All rights reserved.
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		pyScss
COMPONENT_VERSION=	1.3.4
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	\
    sha256:d0323110ecc7d3ead6b99cfec31301306928130e4d0a9eb13226bf390aba8c0e
COMPONENT_ARCHIVE_URL=	$(call pypi_url)
COMPONENT_PROJECT_URL=	https://github.com/Kronuz/pyScss
COMPONENT_BUGDB=	python-mod/pyscss
COMPONENT_ANITYA_ID=	13208

TPNO=			28002

# As per PSARC/2019/093, this component will soon be removed
# This component is not yet built for Python 3.7
PYTHON_VERSIONS = $(WITHOUT_PYTHON3.7)

include $(WS_MAKE_RULES)/prep.mk
include $(WS_MAKE_RULES)/setup.py.mk
include $(WS_MAKE_RULES)/ips.mk

ASLR_MODE = $(ASLR_NOT_APPLICABLE)

COMPONENT_POST_INSTALL_ACTION = \
    (cd $(PROTO_DIR)/usr/bin ; $(MV) -f pyscss pyscss-$(PYTHON_VERSION))

# common targets
build:		$(BUILD_32_and_64)

install:	$(INSTALL_32_and_64)

# The tarball for this version does not ship unittests.
test:		$(NO_TESTS)

system-test:	$(NO_TESTS)

REQUIRED_PACKAGES += library/pcre
REQUIRED_PACKAGES += library/python/pytest-27
REQUIRED_PACKAGES += library/python/setuptools-27
REQUIRED_PACKAGES += system/library
