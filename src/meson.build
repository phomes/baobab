glib_dep = dependency('glib-2.0', version : '>= 2.39.90')
gio_dep = dependency('gio-2.0', version : '>= 2.30.0')
gtk_dep = dependency('gtk+-3.0', version : '>= 3.19.1')
gio_unix_dep = dependency('gio-unix-2.0')

cc = meson.get_compiler('c')
m_dep = cc.find_library('m', required : false)

gnome = import('gnome')
resources = gnome.compile_resources('baobab-resources', 'baobab.gresource.xml', source_dir : '.')

sources = [
    'baobab-application.vala',
    'baobab-cellrenderers.vala',
    'baobab-chart.vala',
    'baobab-location-list.vala',
    'baobab-location.vala',
    'baobab-ringschart.vala',
    'baobab-scanner.vala',
    'baobab-treemap.vala',
    'baobab-window.vala',
    'config.vapi',
    'main.vala',
    resources
]

executable(
    'baobab',
    sources : sources,
    dependencies : [ glib_dep, gio_dep, gio_unix_dep, gtk_dep, m_dep ],
    c_args : [ '-DVERSION="' + meson.project_version() + '"',
               '-DGETTEXT_PACKAGE="baobab"',
               '-DGNOMELOCALEDIR="' + get_option('prefix') + '/' + get_option('localedir') + '"' ],
    vala_args : [ '--gresources=' + meson.current_source_dir() + '/baobab.gresource.xml' ],
    link_args : [ '-rdynamic' ],
    install : true
)

