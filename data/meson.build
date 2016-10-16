cdata = configuration_data()
cdata.set('VERSION', meson.project_version())
cdata.set('bindir', get_option('prefix') + '/' + get_option('bindir'))

msgfmt = find_program('msgfmt')

desktop_file_in = configure_file(
    input : 'org.gnome.baobab.desktop.in.in',
    output : 'org.gnome.baobab.desktop.in',
    configuration : cdata)

custom_target('org.gnome.baobab.desktop',
    input : desktop_file_in,
    output : 'org.gnome.baobab.desktop',
    command : [msgfmt, '--desktop', '--template', '@INPUT@', '-d', meson.current_source_dir() + '/po', '-o', '@OUTPUT@'],
    install : true,
    install_dir : get_option('datadir') + '/applications')

custom_target('org.gnome.baobab.appdata.xml',
    input : 'org.gnome.baobab.appdata.xml.in',
    output : 'org.gnome.baobab.appdata.xml',
    command : [msgfmt, '--xml', '--template', '@INPUT@', '-d', meson.current_source_dir() + '/po', '-o', '@OUTPUT@'],
    install : true,
    install_dir : get_option('datadir') + '/appdata')

configure_file(
    input : 'org.gnome.baobab.service.in',
    output : 'org.gnome.baobab.service',
    install : true,
    install_dir : get_option('datadir') + '/dbus-1/services',
    configuration : cdata)

install_data('org.gnome.baobab.gschema.xml', install_dir : get_option('datadir') + '/glib-2.0/schemas/')
install_man('baobab.1')

