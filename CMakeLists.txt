cmake_minimum_required( VERSION 3.0 )
enable_language( CXX )

find_package( ZLIB REQUIRED )
find_package( SFML 2 REQUIRED system window audio graphics )
find_package( Boost REQUIRED filesystem )

find_package( PkgConfig REQUIRED )
pkg_check_modules( TGUI REQUIRED tgui )

add_definitions( "-DTIXML_USE_TICPP" )
add_definitions( "-include global.hpp" )
#add_definitions( "-include sounds.hpp" )

include_directories( src )
include_directories( src/pcedit )
include_directories( src/scenario )
include_directories( src/game )
include_directories( src/dialogxml )
include_directories( src/dialogxml/widgets)
include_directories( src/dialogxml/dialogs)
include_directories( src/gfx )
include_directories( src/scenedit )
include_directories( src/tools )
include_directories( src/doxy )
include_directories( src/universe )
include_directories( src/fileio )
include_directories( src/fileio/gzstream )
include_directories( src/fileio/resmgr )
include_directories( src/fileio/xml-parser )

include_directories( ${SFML_INCLUDE_DIR} )

file( GLOB_RECURSE CBOE_SRC
	./src/pcedit/pc.editors.cpp

	./src/scenario/item.cpp
	./src/scenario/scenario.cpp
	./src/scenario/monster.cpp
	./src/scenario/town.cpp
	./src/scenario/vehicle.cpp
	./src/scenario/outdoors.cpp
	./src/scenario/shop.cpp
	./src/scenario/special.cpp
	./src/scenario/talking.cpp
	./src/scenario/terrain.cpp
	./src/game/boe.graphutil.cpp
	./src/game/boe.graphics.cpp
	./src/game/boe.ui.cpp
	./src/game/boe.locutils.cpp
	./src/game/boe.menus.linux.cpp
	./src/game/boe.monster.cpp
	./src/game/boe.items.cpp
	./src/game/boe.town.cpp
	./src/game/boe.dlgutil.cpp
	./src/game/boe.townspec.cpp
	./src/game/boe.fileio.cpp
	./src/game/boe.specials.cpp
	./src/game/boe.menu.cpp
	./src/game/boe.main.cpp
	./src/game/boe.party.cpp
	./src/game/boe.actions.cpp
	./src/game/boe.newgraph.cpp
	./src/game/boe.combat.cpp
	./src/game/boe.startup.cpp
	./src/game/boe.text.cpp
	./src/game/boe.infodlg.cpp
	./src/dialogxml/widgets/scrollpane.cpp
	./src/dialogxml/widgets/stack.cpp
	./src/dialogxml/widgets/message.cpp
	./src/dialogxml/widgets/basicbtns.cpp
	./src/dialogxml/widgets/button.cpp
	./src/dialogxml/widgets/field.cpp
	./src/dialogxml/widgets/scrollbar.cpp
	./src/dialogxml/widgets/control.cpp
	./src/dialogxml/widgets/pict.cpp
	./src/dialogxml/dialogs/3choice.cpp
	./src/dialogxml/dialogs/pictchoice.cpp
	./src/dialogxml/dialogs/dialog.cpp
	./src/dialogxml/dialogs/strdlog.cpp
	./src/dialogxml/dialogs/strchoice.cpp
	./src/dialogxml/dialogs/choicedlog.cpp
	./src/spell.cpp
	./src/oldstructs.cpp
	./src/sounds.cpp
	./src/gfx/qdpict.mac.cpp
	./src/gfx/render_text.cpp
	./src/gfx/tiling.cpp
	./src/gfx/gfxsheets.cpp
	./src/gfx/render_shapes.cpp
	./src/gfx/render_image.cpp
	./src/tools/prefs.win.cpp
	./src/tools/drawable_manager.cpp
	./src/tools/cursors.linux.cpp
	./src/tools/framerate_limiter.cpp
	./src/tools/winutil.linux.cpp
	./src/tools/undo.cpp
	./src/location.cpp
	./src/utility.cpp
	./src/universe/creature.cpp
	./src/universe/population.cpp
	./src/universe/living.cpp
	./src/universe/pc.cpp
	./src/universe/party.cpp
	./src/universe/universe.cpp
	./src/mathutil.cpp
	./src/porting.cpp
	./src/fileio/gzstream/gzstream.cpp
	./src/fileio/tarball.cpp
	./src/fileio/special_parse.cpp
	./src/fileio/fileio_party.cpp
	./src/fileio/fileio.cpp
	./src/fileio/resmgr/res_sound.cpp
	./src/fileio/resmgr/res_font.cpp
	./src/fileio/resmgr/res_cursor.cpp
	./src/fileio/resmgr/res_image.cpp
	./src/fileio/resmgr/res_strings.cpp
	./src/fileio/estreams.cpp
	./src/fileio/xml-parser/ticpp.cpp
	./src/fileio/xml-parser/tinyprint.cpp
	./src/fileio/xml-parser/tinyxmlerror.cpp
	./src/fileio/xml-parser/tinyxmlparser.cpp
	./src/fileio/xml-parser/tinyxml.cpp
	./src/fileio/xml-parser/tinystr.cpp
	./src/fileio/fileio_scen.cpp
	./src/fileio/map_parse.cpp
	./src/view_dialogs.cpp
	)

add_executable( cboe "${CBOE_SRC}" )
target_link_libraries( cboe X11 Xcursor GL ${Boost_LIBRARIES} ${CBOE_LIBRARIES} ${ZLIB_LIBRARIES} ${TGUI_LIBRARIES} sfml-graphics sfml-window sfml-audio sfml-network sfml-system )
