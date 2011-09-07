
#-------------------------------------------------------------------------------
# Include the subcomponents
#-------------------------------------------------------------------------------
include( XrdUtils )
include( XrdCrypto )

include( XrdSec )

if( OPENSSL_FOUND )
include( XrdSecgsi )
endif()

if( KERBEROS5_FOUND )
include( XrdSeckrb5 )
endif()

include( XrdClient )

include( XrdOfs )
include( XrdServer )
include( XrdDaemons )
include( XrdFrm )

include( XrdPosix )
include( XrdFfs )
include( XrdPlugins )
include( XrdApps )
include( XrdCns )

#-------------------------------------------------------------------------------
# Install the version and the protocol headers
#-------------------------------------------------------------------------------
install(
  DIRECTORY      XProtocol/
  DESTINATION    ${CMAKE_INSTALL_INCLUDEDIR}/xrootd/XProtocol
  FILES_MATCHING
  PATTERN "*.hh" )

install(
  FILES
  ${CMAKE_BINARY_DIR}/src/XrdVersion.hh
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/xrootd
  PERMISSIONS OWNER_READ OWNER_WRITE )

#-------------------------------------------------------------------------------
# Install the utility scripts
#-------------------------------------------------------------------------------
install(
  FILES
  ${CMAKE_SOURCE_DIR}/utils/XrdOlbNotify.pm
  ${CMAKE_SOURCE_DIR}/utils/fs_stat
  ${CMAKE_SOURCE_DIR}/utils/mps_MigrPurg
  ${CMAKE_SOURCE_DIR}/utils/mps_PreStage
  ${CMAKE_SOURCE_DIR}/utils/mps_Stage
  ${CMAKE_SOURCE_DIR}/utils/mps_Xeq
  ${CMAKE_SOURCE_DIR}/utils/mps_prep
  ${CMAKE_SOURCE_DIR}/utils/xrdcksum
  ${CMAKE_SOURCE_DIR}/utils/xrdmd5sum
  ${CMAKE_SOURCE_DIR}/utils/XrdCmsNotify.pm
  ${CMAKE_SOURCE_DIR}/utils/netchk
  ${CMAKE_SOURCE_DIR}/utils/ooss_CAlloc.pm
  ${CMAKE_SOURCE_DIR}/utils/ooss_Lock.pm
  ${CMAKE_SOURCE_DIR}/utils/ooss_MonP.pm
  ${CMAKE_SOURCE_DIR}/utils/ooss_name2name.pm
  ${CMAKE_SOURCE_DIR}/utils/mps_monStage.pm
  DESTINATION ${CMAKE_INSTALL_DATADIR}/xrootd/utils
  PERMISSIONS OWNER_READ OWNER_WRITE )