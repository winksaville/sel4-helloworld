#
# Copyright 2014, NICTA
#
# This software may be distributed and modified according to the terms of
# the BSD 2-Clause license. Note that NO WARRANTY is provided.
# See "LICENSE_BSD2.txt" for details.
#
# @TAG(NICTA_BSD)
#

apps-$(CONFIG_APP_HELLOWORLD)        += helloworld

# list of libraries the app needs to build
helloworld-y = common libsel4 libmuslc libsel4vka libcpio libelf \
  libsel4allocman \
  libsel4platsupport libsel4platsupport libsel4muslcsys \
  libsel4simple libsel4vspace libsel4utils libutils

# set up correct simple lib for our kernel
ifdef CONFIG_KERNEL_STABLE
helloworld-$(CONFIG_LIB_SEL4_SIMPLE_STABLE) += libsel4simple-stable
else
helloworld-$(CONFIG_LIB_SEL4_SIMPLE_DEFAULT) += libsel4simple-default
endif

helloworld: kernel_elf $(helloworld-y)
