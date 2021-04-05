# SPDX-License-Identifier: GPL-2.0
#
# Makefile for the HID driver
#
hid-y		:= hid-core.o hid-input.o hid-quirks.o

hid-y		+= hid-debug.o

hid-y		+= hid.o
hid-y		+= uhid.o

hid-y		+= hid-generic.o

hid-y		+= hidraw.o

hid-wiimote-y	:= hid-wiimote-core.o hid-wiimote-modules.o hid-wiimote-debug.o

obj-m		+= hid-nintendo.o hid-wiimote.o
