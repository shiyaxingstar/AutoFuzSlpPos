set(shape_srcs ReadOutlets.cpp)
set(common_srcs commonLib.cpp tiffIO.cpp)

set(CONNECTDOWNFILES ConnectDownmn.cpp ConnectDown.cpp ${common_srcs} ${shape_srcs})
set(D8FILES aread8mn.cpp aread8.cpp ${common_srcs} ${shape_srcs})
set(DINFFILES areadinfmn.cpp areadinf.cpp ${common_srcs} ${shape_srcs})
set(D8 D8FlowDirmn.cpp d8.cpp Node.cpp ${common_srcs} ${shape_srcs})
set(D8EXTREAMUP D8flowpathextremeup.cpp D8FlowPathExtremeUpmn.cpp
        ${common_srcs} ${shape_srcs})
set(D8HDIST D8HDistToStrm.cpp D8HDistToStrmmn.cpp ${common_srcs})
set(D8DISTDOWN D8DistDownToStream.cpp D8DistDownToStreammn.cpp ${common_srcs})
set(DINFAVA DinfAvalanche.cpp DinfAvalanchemn.cpp ${common_srcs})
set(DINFCONCLIM DinfConcLimAccum.cpp DinfConcLimAccummn.cpp
        ${common_srcs} ${shape_srcs})
set(DINFDECAY dinfdecayaccum.cpp DinfDecayAccummn.cpp
        ${common_srcs} ${shape_srcs})
set(DINFDISTDOWN DinfDistDown.cpp DinfDistDownmn.cpp ${common_srcs})
set(DINFDISTUP DinfDistUp.cpp DinfDistUpmn.cpp ${common_srcs})
set(DINF DinfFlowDirmn.cpp dinf.cpp Node.cpp
        ${common_srcs} ${shape_srcs})
set(DINFREVACCUM DinfRevAccum.cpp DinfRevAccummn.cpp ${common_srcs})
set(DINFTRANSLIMACCUM DinfTransLimAccum.cpp DinfTransLimAccummn.cpp
        ${common_srcs} ${shape_srcs})
set(DINFUPDEPEND DinfUpDependence.cpp DinfUpDependencemn.cpp ${common_srcs})
set(DROPANALYSISFILES DropAnalysis.cpp DropAnalysismn.cpp
        ${common_srcs} ${shape_srcs})
set(GRIDNET gridnetmn.cpp gridnet.cpp
        ${common_srcs} ${shape_srcs})
set(LENGTHAREA LengthArea.cpp LengthAreamn.cpp ${common_srcs})
set(MVOUTLETSTOSTRMFILES MoveOutletsToStrm.cpp MoveOutletsToStrmmn.cpp
        ${common_srcs} ${shape_srcs})
set(PEUKERDOUGLAS PeukerDouglas.cpp PeukerDouglasmn.cpp ${common_srcs})
set(PITREMOVE flood.cpp PitRemovemn.cpp ${common_srcs})
set(SLOPEAREA SlopeArea.cpp SlopeAreamn.cpp ${common_srcs})
set(SLOPEAREARATIO SlopeAreaRatio.cpp SlopeAreaRatiomn.cpp ${common_srcs})
set(SLOPEAVEDOWN SlopeAveDown.cpp SlopeAveDownmn.cpp ${common_srcs})
set(STREAMNET streamnetmn.cpp streamnet.cpp
        ${common_srcs} ${shape_srcs})
set(THRESHOLD Threshold.cpp Thresholdmn.cpp ${common_srcs})
set(GAGEWATERSHED gagewatershedmn.cpp gagewatershed.cpp ${common_srcs}
        ${shape_srcs})
set(TWI TWImn.cpp TWI.cpp ${common_srcs} ${shape_srcs})

add_executable(aread8 ${D8FILES})
add_executable(areadinf ${DINFFILES})
add_executable(connectdown ${CONNECTDOWNFILES})
add_executable(d8flowdir ${D8})
add_executable(d8flowpathextremeup ${D8EXTREAMUP})
add_executable(d8hdisttostrm ${D8HDIST})
add_executable(d8distdowntostream ${D8DISTDOWN})
add_executable(dinfavalanche ${DINFAVA})
add_executable(dinfconclimaccum ${DINFCONCLIM})
add_executable(dinfdecayaccum ${DINFDECAY})
add_executable(dinfdistdown ${DINFDISTDOWN})
add_executable(dinfdistup ${DINFDISTUP})
add_executable(dinfflowdir ${DINF})
add_executable(dinfrevaccum ${DINFREVACCUM})
add_executable(dinftranslimaccum ${DINFTRANSLIMACCUM})
add_executable(dinfupdependence ${DINFUPDEPEND})
add_executable(dropanalysis ${DROPANALYSISFILES})
add_executable(gridnet ${GRIDNET})
add_executable(lengtharea ${LENGTHAREA})
add_executable(moveoutletstostrm ${MVOUTLETSTOSTRMFILES})
add_executable(peukerdouglas ${PEUKERDOUGLAS})
add_executable(pitremove ${PITREMOVE})
add_executable(slopearea ${SLOPEAREA})
add_executable(slopearearatio ${SLOPEAREARATIO})
add_executable(slopeavedown ${SLOPEAVEDOWN})
add_executable(streamnet ${STREAMNET})
add_executable(threshold ${THRESHOLD})
add_executable(gagewatershed ${GAGEWATERSHED})
add_executable(twi ${TWI})

set(TAUDEM_APP aread8
        areadinf
        connectdown
        d8flowdir
        d8flowpathextremeup
        d8hdisttostrm
        d8distdowntostream
        dinfavalanche
        dinfconclimaccum
        dinfdecayaccum
        dinfdistdown
        dinfdistup
        dinfflowdir
        dinfrevaccum
        dinftranslimaccum
        dinfupdependence
        dropanalysis
        gridnet
        lengtharea
        moveoutletstostrm
        peukerdouglas
        pitremove
        slopearea
        slopearearatio
        slopeavedown
        streamnet
        threshold
        gagewatershed
        twi
        )
foreach (c_target ${TAUDEM_APP})
    target_link_libraries(${c_target} ${MPI_LIBRARIES} ${GDAL_LIBRARIES})
    install(TARGETS ${c_target} DESTINATION ${INSTALL_DIR})
    IF (MSVC)
        SET_PROPERTY(TARGET ${c_target} PROPERTY FOLDER "TauDEM")
    ENDIF ()
endforeach (c_target ${TAUDEM_APP})
