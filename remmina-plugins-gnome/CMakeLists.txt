# remmina-plugins-gnome - The GTK+ Remote Desktop Client
#
# Copyright (C) 2011 Marc-Andre Moreau
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, 
# Boston, MA 02111-1307, USA.
#
# In addition, as a special exception, the copyright holders give
# permission to link the code of portions of this program with the
# OpenSSL library under certain conditions as described in each
# individual source file, and distribute linked combinations
# including the two.
# You must obey the GNU General Public License in all respects
# for all of the code used other than OpenSSL. If you modify
# file(s) with this exception, you may extend this exception to your
# version of the file(s), but you are not obligated to do so. If you
# do not wish to do so, delete this exception statement from your
# version. If you delete this exception statement from all source
# files in the program, then also delete it here.


find_suggested_package(GNOMEKEYRING)
if(GNOMEKEYRING_FOUND)
	set(REMMINA_PLUGINS_GNOME_SRCS
		src/gkeyring_plugin.c
		)

	add_library(remmina-plugins-gnome ${REMMINA_PLUGINS_GNOME_SRCS})
	set_target_properties(remmina-plugins-gnome PROPERTIES PREFIX "")
	set_target_properties(remmina-plugins-gnome PROPERTIES NO_SONAME 1)

	include_directories(${GTK_INCLUDE_DIRS})
	target_link_libraries(remmina-plugins-gnome ${GTK_LIBRARY_DIRS})

		include_directories(${GNOMEKEYRING_INCLUDE_DIRS})
		target_link_libraries(remmina-plugins-gnome ${GNOMEKEYRING_LIBRARIES})

	install(TARGETS remmina-plugins-gnome DESTINATION ${REMMINA_PLUGINDIR})
endif()
