# SPDX-License-Identifier: GPL-2.0-or-later

set(INC
  ../include
  ../../blenfont
  ../../blenkernel
  ../../blenlib
  ../../blentranslation
  ../../bmesh
  ../../depsgraph
  ../../functions
  ../../gpu
  ../../makesdna
  ../../makesrna
  ../../nodes
  ../../windowmanager
  ../../../../intern/glew-mx
  ../../../../intern/guardedalloc
)

set(SRC
  space_spreadsheet.cc
  spreadsheet_cache.cc
  spreadsheet_column.cc
  spreadsheet_context.cc
  spreadsheet_data_source.cc
  spreadsheet_data_source_geometry.cc
  spreadsheet_dataset_draw.cc
  spreadsheet_draw.cc
  spreadsheet_layout.cc
  spreadsheet_ops.cc
  spreadsheet_panels.cc
  spreadsheet_row_filter.cc
  spreadsheet_row_filter_ui.cc

  spreadsheet_cache.hh
  spreadsheet_column.hh
  spreadsheet_column_values.hh
  spreadsheet_context.hh
  spreadsheet_data_source.hh
  spreadsheet_data_source_geometry.hh
  spreadsheet_dataset_draw.hh
  spreadsheet_draw.hh
  spreadsheet_intern.hh
  spreadsheet_layout.hh
  spreadsheet_row_filter.hh
  spreadsheet_row_filter_ui.hh
)

set(LIB
)

if(WITH_OPENVDB)
  list(APPEND INC_SYS
    ${OPENVDB_INCLUDE_DIRS}
  )
  list(APPEND LIB
    ${OPENVDB_LIBRARIES}
  )
  add_definitions(-DWITH_OPENVDB ${OPENVDB_DEFINITIONS})
endif()

blender_add_lib(bf_editor_space_spreadsheet "${SRC}" "${INC}" "${INC_SYS}" "${LIB}")
