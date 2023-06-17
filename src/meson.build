laser_sources = [
  'main.c',
  'laser-application.c',
  'laser-window.c',
]

laser_deps = [
  dependency('gtk4'),
  dependency('libadwaita-1', version: '>= 1.2'),
]

blueprints = custom_target('blueprints',
  input: files(
    'gtk/help-overlay.blp',
    'laser-window.blp',
  ),
  output: '.',
  command: [find_program('blueprint-compiler'), 'batch-compile', '@OUTPUT@', '@CURRENT_SOURCE_DIR@', '@INPUT@'],
)

laser_sources += gnome.compile_resources('laser-resources',
  'laser.gresource.xml',
  c_name: 'laser',
  dependencies: blueprints
)

executable('laser', laser_sources,
  dependencies: laser_deps,
       install: true,
)
