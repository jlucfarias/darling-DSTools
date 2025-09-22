project(DSTools)

add_compile_options(
	-nostdinc
)

#add_darling_executable(dsmemberutil dsmbrutil/dsmbrutil.c)

# Disabling in favor of stub
#install(TARGETS dsmemberutil DESTINATION libexec/darling/usr/bin)

install(FILES
	dirt/dirt.1
	dscacheutil/dscacheutil.1
	dscacheutil/lookupd.1
	dscl/dscl.1
	dsconfigldap/dsconfigldap.1
	dsmbrutil/dsmemberutil.1
	dsmbrutil/memberd.1

	DESTINATION libexec/darling/usr/share/man/man1
)

add_darling_executable(dseditgroup
	ugtools/dseditgroup.c
	commonC/dstools_version.c
)
target_link_libraries(dseditgroup
	CoreFoundation
	OpenDirectory
)
target_include_directories(dseditgroup
	PRIVATE
		"${CMAKE_CURRENT_SOURCE_DIR}/commonC"
)
install(TARGETS dseditgroup DESTINATION libexec/darling/usr/sbin)
install(FILES
	ugtools/dseditgroup.8

	DESTINATION libexec/darling/usr/share/man/man8
)

#add_darling_executable(dscl
#	dscl/dscl.m
#	dscl/PathManager.m
#	dscl/PathDirService.m
#	dscl/PathNode.m
#	dscl/PathNodeConfig.m
#	dscl/PathNodeSearch.m
#	dscl/PathRecord.m
#	dscl/PathRecordConfig.m
#	dscl/PathRecordType.m
#	dscl/PathRecordTypeConfig.m
#	dscl/PathItem.m
#	dscl/PlugInManager.m
#	dscl/NSStringEscPath.m
#	DSObjCWrappers/DSoAttributeUtils.m
#	DSObjCWrappers/DSoGroup.m
#	DSObjCWrappers/DSoException.m
#	DSObjCWrappers/DSoStatus.m
#	DSObjCWrappers/DSoDirectory.m
#	DSObjCWrappers/DSoBuffer.m
#	DSObjCWrappers/DSoDataList.m
#	DSObjCWrappers/DSoDataNode.m
#	DSObjCWrappers/DSoNode.m
#	DSObjCWrappers/DSoNodeConfig.m
#	DSObjCWrappers/DSoNodeBrowserItem.m
#	DSObjCWrappers/DSoRecord.m
#	DSObjCWrappers/DSoUser.m
#	commonC/dstools_version.c
#)
#target_link_libraries(dscl
#	Foundation
#	DirectoryService
#	opendirectory_internal
#	edit
#)
#target_include_directories(dscl
#	PRIVATE
#		"${CMAKE_CURRENT_SOURCE_DIR}/commonC"
#		"${CMAKE_CURRENT_SOURCE_DIR}/DSObjCWrappers"
#		"${CMAKE_CURRENT_SOURCE_DIR}/dscl"
#)
#install(TARGETS dscl DESTINATION libexec/darling/usr/bin)
#install(FILES
#	dscl/dscl.1
#
#	DESTINATION libexec/darling/usr/share/man/man1
#)

install(FILES
	dsenableroot/dsenableroot.8
	dserr/dserr.8
	pwpolicy/pwpolicy.8

	DESTINATION libexec/darling/usr/share/man/man8
)
