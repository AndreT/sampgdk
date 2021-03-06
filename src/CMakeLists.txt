add_subdirectory(internal)

set(SAMPGDK_DEF_FILE ${CMAKE_CURRENT_BINARY_DIR}/sampgdk.def)
set(SAMPGDK_SYM_FILE ${CMAKE_CURRENT_BINARY_DIR}/sampgdk.sym)

sampgdk_add_sources(
  a_http.c
  a_http.idl
  a_objects.c
  a_objects.idl
  a_players.c
  a_players.idl
  a_samp.c
  a_samp.idl
  a_vehicles.c
  a_vehicles.idl
  core.api
  core.c
  interop.api
  interop.c
  sampgdk.rc
  version.api
  version.c
)

if(WIN32)
  sampgdk_add_sources(${SAMPGDK_DEF_FILE})
elseif(UNIX)
  sampgdk_add_sources(${SAMPGDK_SYM_FILE})
endif()

# These variables are used at the upper level.
if(WIN32)
  set(SAMPGDK_DEF_FILE ${SAMPGDK_DEF_FILE} PARENT_SCOPE)
elseif(UNIX)
  set(SAMPGDK_SYM_FILE ${SAMPGDK_SYM_FILE} PARENT_SCOPE)
endif()
