project( calamares-netrunner-branding )

# The partition manager uses ECM but ECMConfig.cmake
# will complain if we require CMake less than 2.8.13,
# so never change this.
cmake_minimum_required( VERSION 2.8.12 )

set( QT_VERSION 5.3.0 )
find_package( Qt5 ${QT_VERSION} CONFIG REQUIRED LinguistTools Quick )

set( CALAMARES_NETRUNNER_BRANDING_TRANSLATION_LANGUAGES en it )

# Better default installation paths: GNUInstallDirs defines
# CMAKE_INSTALL_FULL_SYSCONFDIR to be CMAKE_INSTALL_PREFIX/etc by default
# but we really want /etc
if( NOT DEFINED CMAKE_INSTALL_SYSCONFDIR )
    set( CMAKE_INSTALL_SYSCONFDIR "/etc" )
endif()

# make predefined install dirs available everywhere
include( GNUInstallDirs )

add_subdirectory( netrunner-debian )

install(
    FILES
        settings.conf
    DESTINATION
        "${CMAKE_INSTALL_SYSCONFDIR}/calamares"
)

install(
  FILES
      calamares.desktop
  DESTINATION
      "${CMAKE_INSTALL_SYSCONFDIR}/skel/Desktop"
)
