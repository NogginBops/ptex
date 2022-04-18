configure_file(PtexVersion.h.in
    ${CMAKE_CURRENT_SOURCE_DIR}/PtexVersion.h @ONLY)

set(SRCS
    PtexCache.cpp
    PtexFilters.cpp
    PtexHalf.cpp
    PtexReader.cpp
    PtexSeparableFilter.cpp
    PtexSeparableKernel.cpp
    PtexTriangleFilter.cpp
    PtexTriangleKernel.cpp
    PtexUtils.cpp
    PtexWriter.cpp)

set(HEADERS 
    PtexExports.h
    PtexHalf.h
    PtexInt.h
    PtexPlatform.h
    Ptexture.h
    PtexUtils.h
    PtexVersion.h)

add_library(Ptex STATIC ${SRCS} ${HEADERS})
#set_target_properties(Ptex PROPERTIES OUTPUT_NAME Ptex)
target_compile_definitions(Ptex PUBLIC PTEX_STATIC)
#target_include_directories(Ptex_static
#PUBLIC
#    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
#PRIVATE
#    ${CMAKE_CURRENT_SOURCE_DIR})
target_link_libraries(Ptex PUBLIC Threads::Threads ZLIB::ZLIB)
#install(TARGETS Ptex_static EXPORT Ptex DESTINATION ${CMAKE_INSTALL_LIBDIR})

target_include_directories(Ptex PUBLIC ${HEADERS})
