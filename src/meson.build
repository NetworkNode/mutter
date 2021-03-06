mutter_includedir = join_paths(pkgincludedir, 'meta')

mutter_includes = [
  include_directories('.'),
  top_includepath,
  clutter_includepath,
  cogl_includepath,
]

mutter_lib_deps = [
  m_dep,
]

mutter_pkg_deps = [
  cairo_dep,
  gio_unix_dep,
  glib_dep,
  gmodule_no_export_dep,
  gnome_desktop_dep,
  gsettings_desktop_schemas_dep,
  gnome_settings_daemon_dep,
  gtk3_dep,
  json_glib_dep,
  pango_dep,
  xkbcommon_dep,
]

if have_gl
  mutter_pkg_deps += [
    gl_dep,
  ]
endif

if have_gles2
  mutter_pkg_deps += [
    gles2_dep,
  ]
endif

if have_egl
  mutter_pkg_deps += [
    egl_dep,
  ]
endif

if have_libgudev
  mutter_pkg_deps += [
    gudev_dep,
    libudev_dep,
  ]
endif

if have_startup_notification
  mutter_pkg_deps += [
    libstartup_notification_dep,
  ]
endif

if have_libcanberra
  mutter_pkg_deps += [
    libcanberra_gtk3_dep,
  ]
endif

if have_libwacom
  mutter_pkg_deps += [
    libwacom_dep,
  ]
endif

if have_remote_desktop
  mutter_pkg_deps += [
    libpipewire_dep,
  ]
endif

if have_introspection
  mutter_pkg_deps += [
    gobject_introspection_dep,
  ]
endif

if have_x11
  mutter_pkg_deps += [
    xrandr_dep,
    x11_dep,
    xinerama_dep,
    xext_dep,
    ice_dep,
    xcomposite_dep,
    xcursor_dep,
    xdamage_dep,
    xext_dep,
    xfixes_dep,
    xi_dep,
    xkbfile_dep,
    xkeyboard_config_dep,
    xkbcommon_x11_dep,
    xrender_dep,
    x11_xcb_dep,
    xcb_randr_dep,
    xcb_res_dep,
  ]

  if have_sm
    mutter_pkg_deps += [
      sm_dep,
    ]
  endif
endif

if have_wayland
  mutter_pkg_deps += [
    wayland_server_dep,
  ]
endif

if have_native_backend
  mutter_pkg_deps += [
    libdrm_dep,
    libinput_dep,
    gudev_dep,
    libgbm_dep,
    logind_provider_dep,
  ]
endif

if have_wayland_eglstream
  mutter_lib_deps += [
    dl_dep,
  ]
  mutter_pkg_deps += [
    wayland_eglstream_protocols_dep,
  ]
endif

mutter_deps = [
  mutter_pkg_deps,
  mutter_lib_deps,
]

mutter_c_args = [
  '-DCLUTTER_ENABLE_COMPOSITOR_API',
  '-DCLUTTER_ENABLE_EXPERIMENTAL_API',
  '-DCOGL_ENABLE_EXPERIMENTAL_API',
  '-DCOGL_ENABLE_EXPERIMENTAL_2_0_API',
  '-DCOGL_ENABLE_MUTTER_API',
  '-DCLUTTER_DISABLE_DEPRECATION_WARNINGS',
  '-DCOGL_DISABLE_DEPRECATION_WARNINGS',
  '-DG_LOG_DOMAIN="mutter"',
  '-DSN_API_NOT_YET_FROZEN=1',
  '-DGETTEXT_PACKAGE="@0@"'.format(meson.project_name()),
]

if get_option('verbose')
  mutter_c_args += [
    '-DWITH_VERBOSE_MODE'
  ]
endif

mutter_sources = [
  'backends/edid.h',
  'backends/edid-parse.c',
  'backends/gsm-inhibitor-flag.h',
  'backends/meta-backend.c',
  'backends/meta-backend-private.h',
  'backends/meta-barrier.c',
  'backends/meta-barrier-private.h',
  'backends/meta-crtc.c',
  'backends/meta-crtc.h',
  'backends/meta-cursor.c',
  'backends/meta-cursor.h',
  'backends/meta-cursor-renderer.c',
  'backends/meta-cursor-renderer.h',
  'backends/meta-cursor-sprite-xcursor.c',
  'backends/meta-cursor-sprite-xcursor.h',
  'backends/meta-cursor-tracker.c',
  'backends/meta-cursor-tracker-private.h',
  'backends/meta-display-config-shared.h',
  'backends/meta-dnd-private.h',
  'backends/meta-gpu.c',
  'backends/meta-gpu.h',
  'backends/meta-idle-monitor.c',
  'backends/meta-idle-monitor-dbus.c',
  'backends/meta-idle-monitor-dbus.h',
  'backends/meta-idle-monitor-private.h',
  'backends/meta-input-settings.c',
  'backends/meta-input-settings-private.h',
  'backends/meta-logical-monitor.c',
  'backends/meta-logical-monitor.h',
  'backends/meta-monitor.c',
  'backends/meta-monitor-config-manager.c',
  'backends/meta-monitor-config-manager.h',
  'backends/meta-monitor-config-migration.c',
  'backends/meta-monitor-config-migration.h',
  'backends/meta-monitor-config-store.c',
  'backends/meta-monitor-config-store.h',
  'backends/meta-monitor.h',
  'backends/meta-monitor-manager.c',
  'backends/meta-monitor-manager-dummy.c',
  'backends/meta-monitor-manager-dummy.h',
  'backends/meta-monitor-manager-private.h',
  'backends/meta-orientation-manager.c',
  'backends/meta-orientation-manager.h',
  'backends/meta-output.c',
  'backends/meta-output.h',
  'backends/meta-pointer-constraint.c',
  'backends/meta-pointer-constraint.h',
  'backends/meta-remote-access-controller-private.h',
  'backends/meta-remote-access-controller.c',
  'backends/meta-renderer.c',
  'backends/meta-renderer.h',
  'backends/meta-renderer-view.c',
  'backends/meta-renderer-view.h',
  'backends/meta-settings.c',
  'backends/meta-settings-private.h',
  'backends/meta-stage.c',
  'backends/meta-stage-private.h',
  'backends/x11/cm/meta-backend-x11-cm.c',
  'backends/x11/cm/meta-backend-x11-cm.h',
  'backends/x11/cm/meta-cursor-sprite-xfixes.c',
  'backends/x11/cm/meta-cursor-sprite-xfixes.h',
  'backends/x11/cm/meta-renderer-x11-cm.c',
  'backends/x11/cm/meta-renderer-x11-cm.h',
  'backends/x11/meta-backend-x11.c',
  'backends/x11/meta-backend-x11.h',
  'backends/x11/meta-barrier-x11.c',
  'backends/x11/meta-barrier-x11.h',
  'backends/x11/meta-clutter-backend-x11.c',
  'backends/x11/meta-clutter-backend-x11.h',
  'backends/x11/meta-crtc-xrandr.c',
  'backends/x11/meta-crtc-xrandr.h',
  'backends/x11/meta-cursor-renderer-x11.c',
  'backends/x11/meta-cursor-renderer-x11.h',
  'backends/x11/meta-gpu-xrandr.c',
  'backends/x11/meta-gpu-xrandr.h',
  'backends/x11/meta-input-settings-x11.c',
  'backends/x11/meta-input-settings-x11.h',
  'backends/x11/meta-monitor-manager-xrandr.c',
  'backends/x11/meta-monitor-manager-xrandr.h',
  'backends/x11/meta-output-xrandr.c',
  'backends/x11/meta-output-xrandr.h',
  'backends/x11/meta-renderer-x11.c',
  'backends/x11/meta-renderer-x11.h',
  'backends/x11/meta-stage-x11-nested.c',
  'backends/x11/meta-stage-x11-nested.h',
  'backends/x11/nested/meta-backend-x11-nested.c',
  'backends/x11/nested/meta-backend-x11-nested.h',
  'backends/x11/nested/meta-cursor-renderer-x11-nested.c',
  'backends/x11/nested/meta-cursor-renderer-x11-nested.h',
  'backends/x11/nested/meta-renderer-x11-nested.c',
  'backends/x11/nested/meta-renderer-x11-nested.h',
  'compositor/clutter-utils.c',
  'compositor/clutter-utils.h',
  'compositor/cogl-utils.c',
  'compositor/cogl-utils.h',
  'compositor/compositor.c',
  'compositor/compositor-private.h',
  'compositor/meta-background-actor.c',
  'compositor/meta-background-actor-private.h',
  'compositor/meta-background.c',
  'compositor/meta-background-group.c',
  'compositor/meta-background-image.c',
  'compositor/meta-background-private.h',
  'compositor/meta-cullable.c',
  'compositor/meta-cullable.h',
  'compositor/meta-dnd-actor.c',
  'compositor/meta-dnd-actor-private.h',
  'compositor/meta-dnd.c',
  'compositor/meta-feedback-actor.c',
  'compositor/meta-feedback-actor-private.h',
  'compositor/meta-module.c',
  'compositor/meta-module.h',
  'compositor/meta-plugin.c',
  'compositor/meta-plugin-manager.c',
  'compositor/meta-plugin-manager.h',
  'compositor/meta-shadow-factory.c',
  'compositor/meta-shaped-texture.c',
  'compositor/meta-shaped-texture-private.h',
  'compositor/meta-surface-actor.c',
  'compositor/meta-surface-actor.h',
  'compositor/meta-surface-actor-x11.c',
  'compositor/meta-surface-actor-x11.h',
  'compositor/meta-sync-ring.c',
  'compositor/meta-sync-ring.h',
  'compositor/meta-texture-rectangle.c',
  'compositor/meta-texture-rectangle.h',
  'compositor/meta-texture-tower.c',
  'compositor/meta-texture-tower.h',
  'compositor/meta-window-actor.c',
  'compositor/meta-window-actor-private.h',
  'compositor/meta-window-group.c',
  'compositor/meta-window-group-private.h',
  'compositor/meta-window-shape.c',
  'compositor/region-utils.c',
  'compositor/region-utils.h',
  'core/bell.c',
  'core/bell.h',
  'core/boxes.c',
  'core/boxes-private.h',
  'core/constraints.c',
  'core/constraints.h',
  'core/core.c',
  'core/core.h',
  'core/delete.c',
  'core/display.c',
  'core/display-private.h',
  'core/edge-resistance.c',
  'core/edge-resistance.h',
  'core/events.c',
  'core/events.h',
  'core/frame.c',
  'core/frame.h',
  'core/keybindings.c',
  'core/keybindings-private.h',
  'core/main.c',
  'core/main-private.h',
  'core/meta-accel-parse.c',
  'core/meta-accel-parse.h',
  'core/meta-border.c',
  'core/meta-border.h',
  'core/meta-close-dialog.c',
  'core/meta-close-dialog-default.c',
  'core/meta-close-dialog-default-private.h',
  'core/meta-fraction.c',
  'core/meta-fraction.h',
  'core/meta-gesture-tracker.c',
  'core/meta-gesture-tracker-private.h',
  'core/meta-inhibit-shortcuts-dialog.c',
  'core/meta-inhibit-shortcuts-dialog-default.c',
  'core/meta-inhibit-shortcuts-dialog-default-private.h',
  'core/meta-workspace-manager.c',
  'core/meta-workspace-manager-private.h',
  'core/place.c',
  'core/place.h',
  'core/prefs.c',
  'core/restart.c',
  'core/stack.c',
  'core/stack.h',
  'core/stack-tracker.c',
  'core/stack-tracker.h',
  'core/startup-notification.c',
  'core/startup-notification-private.h',
  'core/util.c',
  'core/util-private.h',
  'core/window.c',
  'core/window-private.h',
  'core/workspace.c',
  'core/workspace-private.h',
  'ui/frames.c',
  'ui/frames.h',
  'ui/theme.c',
  'ui/theme-private.h',
  'ui/ui.c',
  'ui/ui.h',
  'x11/atomnames.h',
  'x11/events.c',
  'x11/events.h',
  'x11/group.c',
  'x11/group-private.h',
  'x11/group-props.c',
  'x11/group-props.h',
  'x11/iconcache.c',
  'x11/iconcache.h',
  'x11/meta-startup-notification-x11.c',
  'x11/meta-startup-notification-x11.h',
  'x11/meta-x11-display.c',
  'x11/meta-x11-display-private.h',
  'x11/meta-x11-errors.c',
  'x11/mutter-Xatomtype.h',
  'x11/session.c',
  'x11/session.h',
  'x11/window-props.c',
  'x11/window-props.h',
  'x11/window-x11.c',
  'x11/window-x11.h',
  'x11/window-x11-private.h',
  'x11/xprops.c',
  'x11/xprops.h',
]

if have_egl
  mutter_sources += [
    'backends/meta-egl.c',
    'backends/meta-egl-ext.h',
    'backends/meta-egl.h',
  ]
endif

if have_gles2
  mutter_sources += [
    'backends/meta-gles3.c',
    'backends/meta-gles3.h',
    'backends/meta-gles3-table.h',
  ]
endif

if have_remote_desktop
  mutter_sources += [
    'backends/meta-dbus-session-watcher.c',
    'backends/meta-dbus-session-watcher.h',
    'backends/meta-remote-desktop.c',
    'backends/meta-remote-desktop.h',
    'backends/meta-remote-desktop-session.c',
    'backends/meta-remote-desktop-session.h',
    'backends/meta-screen-cast.c',
    'backends/meta-screen-cast.h',
    'backends/meta-screen-cast-monitor-stream.c',
    'backends/meta-screen-cast-monitor-stream.h',
    'backends/meta-screen-cast-monitor-stream-src.c',
    'backends/meta-screen-cast-monitor-stream-src.h',
    'backends/meta-screen-cast-session.c',
    'backends/meta-screen-cast-session.h',
    'backends/meta-screen-cast-stream.c',
    'backends/meta-screen-cast-stream.h',
    'backends/meta-screen-cast-stream-src.c',
    'backends/meta-screen-cast-stream-src.h',
  ]
endif

if have_wayland
  mutter_sources += [
    'compositor/meta-surface-actor-wayland.c',
    'compositor/meta-surface-actor-wayland.h',
    'wayland/meta-cursor-sprite-wayland.c',
    'wayland/meta-cursor-sprite-wayland.h',
    'wayland/meta-pointer-confinement-wayland.c',
    'wayland/meta-pointer-confinement-wayland.h',
    'wayland/meta-pointer-lock-wayland.c',
    'wayland/meta-pointer-lock-wayland.h',
    'wayland/meta-wayland-actor-surface.c',
    'wayland/meta-wayland-actor-surface.h',
    'wayland/meta-wayland-buffer.c',
    'wayland/meta-wayland-buffer.h',
    'wayland/meta-wayland.c',
    'wayland/meta-wayland-cursor-surface.c',
    'wayland/meta-wayland-cursor-surface.h',
    'wayland/meta-wayland-data-device.c',
    'wayland/meta-wayland-data-device.h',
    'wayland/meta-wayland-data-device-private.h',
    'wayland/meta-wayland-dma-buf.c',
    'wayland/meta-wayland-dma-buf.h',
    'wayland/meta-wayland-gtk-shell.c',
    'wayland/meta-wayland-gtk-shell.h',
    'wayland/meta-wayland.h',
    'wayland/meta-wayland-inhibit-shortcuts.c',
    'wayland/meta-wayland-inhibit-shortcuts-dialog.c',
    'wayland/meta-wayland-inhibit-shortcuts-dialog.h',
    'wayland/meta-wayland-inhibit-shortcuts.h',
    'wayland/meta-wayland-input-device.c',
    'wayland/meta-wayland-input-device.h',
    'wayland/meta-wayland-keyboard.c',
    'wayland/meta-wayland-keyboard.h',
    'wayland/meta-wayland-legacy-xdg-shell.c',
    'wayland/meta-wayland-legacy-xdg-shell.h',
    'wayland/meta-wayland-outputs.c',
    'wayland/meta-wayland-outputs.h',
    'wayland/meta-wayland-pointer.c',
    'wayland/meta-wayland-pointer-constraints.c',
    'wayland/meta-wayland-pointer-constraints.h',
    'wayland/meta-wayland-pointer-gesture-pinch.c',
    'wayland/meta-wayland-pointer-gesture-pinch.h',
    'wayland/meta-wayland-pointer-gestures.c',
    'wayland/meta-wayland-pointer-gestures.h',
    'wayland/meta-wayland-pointer-gesture-swipe.c',
    'wayland/meta-wayland-pointer-gesture-swipe.h',
    'wayland/meta-wayland-pointer.h',
    'wayland/meta-wayland-popup.c',
    'wayland/meta-wayland-popup.h',
    'wayland/meta-wayland-private.h',
    'wayland/meta-wayland-region.c',
    'wayland/meta-wayland-region.h',
    'wayland/meta-wayland-seat.c',
    'wayland/meta-wayland-seat.h',
    'wayland/meta-wayland-shell-surface.c',
    'wayland/meta-wayland-shell-surface.h',
    'wayland/meta-wayland-subsurface.c',
    'wayland/meta-wayland-subsurface.h',
    'wayland/meta-wayland-surface.c',
    'wayland/meta-wayland-surface.h',
    'wayland/meta-wayland-tablet.c',
    'wayland/meta-wayland-tablet-cursor-surface.c',
    'wayland/meta-wayland-tablet-cursor-surface.h',
    'wayland/meta-wayland-tablet.h',
    'wayland/meta-wayland-tablet-manager.c',
    'wayland/meta-wayland-tablet-manager.h',
    'wayland/meta-wayland-tablet-pad.c',
    'wayland/meta-wayland-tablet-pad-group.c',
    'wayland/meta-wayland-tablet-pad-group.h',
    'wayland/meta-wayland-tablet-pad.h',
    'wayland/meta-wayland-tablet-pad-ring.c',
    'wayland/meta-wayland-tablet-pad-ring.h',
    'wayland/meta-wayland-tablet-pad-strip.c',
    'wayland/meta-wayland-tablet-pad-strip.h',
    'wayland/meta-wayland-tablet-seat.c',
    'wayland/meta-wayland-tablet-seat.h',
    'wayland/meta-wayland-tablet-tool.c',
    'wayland/meta-wayland-tablet-tool.h',
    'wayland/meta-wayland-text-input.c',
    'wayland/meta-wayland-text-input.h',
    'wayland/meta-wayland-text-input-legacy.c',
    'wayland/meta-wayland-text-input-legacy.h',
    'wayland/meta-wayland-touch.c',
    'wayland/meta-wayland-touch.h',
    'wayland/meta-wayland-types.h',
    'wayland/meta-wayland-versions.h',
    'wayland/meta-wayland-wl-shell.c',
    'wayland/meta-wayland-wl-shell.h',
    'wayland/meta-wayland-xdg-foreign.c',
    'wayland/meta-wayland-xdg-foreign.h',
    'wayland/meta-wayland-xdg-shell.c',
    'wayland/meta-wayland-xdg-shell.h',
    'wayland/meta-window-wayland.c',
    'wayland/meta-window-wayland.h',
    'wayland/meta-window-xwayland.c',
    'wayland/meta-window-xwayland.h',
    'wayland/meta-xwayland.c',
    'wayland/meta-xwayland-grab-keyboard.c',
    'wayland/meta-xwayland-grab-keyboard.h',
    'wayland/meta-xwayland.h',
    'wayland/meta-xwayland-private.h',
    'wayland/meta-xwayland-selection.c',
    'wayland/meta-xwayland-selection-private.h',
  ]
endif

if have_native_backend
  mutter_sources += [
    'backends/native/dbus-utils.c',
    'backends/native/dbus-utils.h',
    'backends/native/meta-backend-native.c',
    'backends/native/meta-backend-native.h',
    'backends/native/meta-backend-native-private.h',
    'backends/native/meta-barrier-native.c',
    'backends/native/meta-barrier-native.h',
    'backends/native/meta-clutter-backend-native.c',
    'backends/native/meta-clutter-backend-native.h',
    'backends/native/meta-crtc-kms.c',
    'backends/native/meta-crtc-kms.h',
    'backends/native/meta-cursor-renderer-native.c',
    'backends/native/meta-cursor-renderer-native.h',
    'backends/native/meta-gpu-kms.c',
    'backends/native/meta-gpu-kms.h',
    'backends/native/meta-input-settings-native.c',
    'backends/native/meta-input-settings-native.h',
    'backends/native/meta-launcher.c',
    'backends/native/meta-launcher.h',
    'backends/native/meta-monitor-manager-kms.c',
    'backends/native/meta-monitor-manager-kms.h',
    'backends/native/meta-output-kms.c',
    'backends/native/meta-output-kms.h',
    'backends/native/meta-renderer-native.c',
    'backends/native/meta-renderer-native-gles3.c',
    'backends/native/meta-renderer-native-gles3.h',
    'backends/native/meta-renderer-native.h',
    'backends/native/meta-stage-native.c',
    'backends/native/meta-stage-native.h',
  ]
endif

if have_wayland_eglstream
  mutter_sources += [
    'wayland/meta-wayland-egl-stream.c',
    'wayland/meta-wayland-egl-stream.h',
  ]
endif

mutter_built_sources = []

dbus_display_config_built_sources = gnome.gdbus_codegen('meta-dbus-display-config',
    'org.gnome.Mutter.DisplayConfig.xml',
    interface_prefix: 'org.gnome.Mutter.',
    namespace: 'MetaDBus',
  )
mutter_built_sources += dbus_display_config_built_sources

dbus_idle_monitor_built_sources = gnome.gdbus_codegen('meta-dbus-idle-monitor',
    'org.gnome.Mutter.IdleMonitor.xml',
    interface_prefix: 'org.gnome.Mutter.',
    namespace: 'MetaDBus',
    object_manager: true,
  )
mutter_built_sources += dbus_idle_monitor_built_sources

if have_native_backend
  gdbus_codegen = find_program('gdbus-codegen')
  dbus_login1_built_sources = custom_target('meta-dbus-login1',
    input: 'org.freedesktop.login1.xml',
    output: [
      'meta-dbus-login1.c',
      'meta-dbus-login1.h',
    ],
    command: [
      gdbus_codegen,
      '--interface-prefix', 'org.freedesktop.login1',
      '--c-namespace', 'Login1',
      '--generate-c-code', 'meta-dbus-login1',
      '--output-directory', join_paths(builddir, 'src'),
      '--c-generate-autocleanup', 'all',
      '@INPUT@',
    ]
  )
  mutter_built_sources += dbus_login1_built_sources
endif

if have_remote_desktop
  dbus_remote_desktop_built_sources = gnome.gdbus_codegen('meta-dbus-remote-desktop',
      'org.gnome.Mutter.RemoteDesktop.xml',
      interface_prefix: 'org.gnome.Mutter.',
      namespace: 'MetaDBus',
    )
  mutter_built_sources += dbus_remote_desktop_built_sources

  dbus_screen_cast_built_sources = gnome.gdbus_codegen('meta-dbus-screen-cast',
      'org.gnome.Mutter.ScreenCast.xml',
      interface_prefix: 'org.gnome.Mutter.',
      namespace: 'MetaDBus',
    )
  mutter_built_sources += dbus_screen_cast_built_sources
endif

cvt = find_program('cvt')

gen_default_modes = find_program('backends/native/gen-default-modes.py')
default_modes_h = custom_target('meta-default-modes',
  output: 'meta-default-modes.h',
  command: [gen_default_modes, '@OUTPUT@']
)
mutter_built_sources += default_modes_h

if have_wayland
  # Format:
  #  - protocol name
  #  - protocol stability ('private', 'stable' or 'unstable')
  #  - protocol version (if stability is 'unstable')
  wayland_protocols = [
    ['gtk-primary-selection', 'private', ],
    ['gtk-shell', 'private', ],
    ['gtk-text-input', 'private', ],
    ['keyboard-shortcuts-inhibit', 'unstable', 'v1', ],
    ['linux-dmabuf', 'unstable', 'v1', ],
    ['pointer-constraints', 'unstable', 'v1', ],
    ['pointer-gestures', 'unstable', 'v1', ],
    ['relative-pointer', 'unstable', 'v1', ],
    ['tablet', 'unstable', 'v2', ],
    ['text-input', 'unstable', 'v3', ],
    ['xdg-foreign', 'unstable', 'v1', ],
    ['xdg-output', 'unstable', 'v1', ],
    ['xdg-shell', 'unstable', 'v6', ],
    ['xdg-shell', 'stable', ],
    ['xwayland-keyboard-grab', 'unstable', 'v1', ],
  ]
  if have_wayland_eglstream
    wayland_eglstream_protocols_dir = wayland_eglstream_protocols_dep.get_pkgconfig_variable('pkgdatadir')
    wayland_protocols += [
      ['wayland-eglstream-controller', 'third-party', wayland_eglstream_protocols_dir],
    ]
  endif

  wayland_scanner = find_program('wayland-scanner')
  protocols_dir = wayland_protocols_dep.get_pkgconfig_variable('pkgdatadir')
  assert(protocols_dir != '', 'Could not get pkgdatadir from wayland-protocols.pc')

  foreach p: wayland_protocols
    protocol_name = p.get(0)
    protocol_type = p.get(1)

    if protocol_type == 'stable'
      output_base = protocol_name
      input = join_paths(protocols_dir,
                         '@0@/@1@/@2@.xml'.format(protocol_type,
                         protocol_name,
                         output_base))
    elif protocol_type == 'private'
      output_base = protocol_name
      input = 'wayland/protocol/@0@.xml'.format(protocol_name)
    elif protocol_type == 'third-party'
      output_base = protocol_name
      protocol_dir = p.get(2)
      input = join_paths(protocol_dir, '@0@.xml'.format(protocol_name))
    else
      protocol_version = p.get(2)
      output_base = '@0@-@1@-@2@'.format(protocol_name,
                                         protocol_type,
                                         protocol_version)
      input = join_paths(protocols_dir,
                         '@0@/@1@/@2@.xml'.format(protocol_type,
                                                  protocol_name,
                                                  output_base))
    endif

    mutter_built_sources += custom_target('@0@ server header'.format(output_base),
      input: input,
      output: '@0@-server-protocol.h'.format(output_base),
      command: [
        wayland_scanner,
        'server-header',
        '@INPUT@', '@OUTPUT@',
      ]
    )

    mutter_built_sources += custom_target('@0@ source'.format(output_base),
      input: input,
      output: '@0@-protocol.c'.format(output_base),
      command: [
        wayland_scanner,
        'private-code',
        '@INPUT@', '@OUTPUT@',
      ]
    )
  endforeach
endif

subdir('meta')

mutter_marshal = gnome.genmarshal('meta-marshal',
  sources: ['meta-marshal.list'],
  prefix: 'meta_marshal',
  internal: true,
)
mutter_built_sources += mutter_marshal

mutter_built_sources += mutter_enum_types
mutter_built_sources += mutter_version

libmutter_name = 'mutter-' + libmutter_api_version
libmutter = shared_library(libmutter_name,
  sources: [
    mutter_sources,
    mutter_built_sources,
  ],
  soversion: '0.0.0',
  include_directories: mutter_includes,
  c_args: mutter_c_args,
  dependencies: [
    libmutter_cogl_dep,
    libmutter_clutter_dep,
    mutter_deps,
  ],
  install_rpath: pkglibdir,
  install_dir: libdir,
  install: true,
)

libmutter_dep = declare_dependency(
  link_with: libmutter,
  include_directories: mutter_includes,
  sources: mutter_built_sources,
  dependencies: [
    libmutter_cogl_dep,
    libmutter_clutter_dep,
    mutter_deps,
  ],
)

executable('mutter',
  sources: [
    files('core/mutter.c'),
  ],
  include_directories: mutter_includes,
  c_args: mutter_c_args,
  dependencies: [libmutter_dep],
  install_dir: bindir,
  install: true,
)

executable('mutter-restart-helper',
  sources: [
    files('core/restart-helper.c'),
  ],
  include_directories: [
    top_includepath,
  ],
  c_args: mutter_c_args,
  dependencies: [
    x11_dep,
    xcomposite_dep,
  ],
  install_dir: libexecdir,
  install: true,
)

if have_introspection
  mutter_introspected_sources = []
  foreach source : mutter_sources
    if source.endswith('.c')
      mutter_introspected_sources += source
    endif
  endforeach

  libmutter_gir = gnome.generate_gir(libmutter,
    sources: [
      mutter_version,
      mutter_enum_types[1],
      mutter_introspected_sources,
      mutter_public_header_files
    ],
    nsversion: libmutter_api_version,
    namespace: 'Meta',
    symbol_prefix: 'meta',
    includes: [
      'GObject-2.0',
      'GDesktopEnums-3.0',
      'Gdk-3.0',
      'Gtk-3.0',
      'xlib-2.0',
      'xfixes-4.0',
      libmutter_cogl_gir[0],
      libmutter_cogl_pango_gir[0],
      libmutter_clutter_gir[0],
    ],
    dependencies: [
      mutter_deps,
      libmutter_dep,
    ],
    extra_args: mutter_c_args + [
      '-U_GNU_SOURCE',
    ],
    install_dir_gir: pkglibdir,
    install_dir_typelib: pkglibdir,
    install: true
  )
endif

pkg.generate(
  name: 'Meta',
  filebase: 'libmutter-' + libmutter_api_version,
  description: 'Mutter compositor and window manager library',
  libraries: [libmutter],
  subdirs: pkgname,
  requires: [mutter_pkg_deps, libmutter_clutter_name],
  version: meson.project_version(),
  variables: [
    'apiversion=' + libmutter_api_version,
    'girdir=${libdir}/mutter-' + libmutter_api_version,
    'typelibdir=${libdir}/mutter-' + libmutter_api_version,
  ],
)

subdir('compositor/plugins')

if have_tests 
  subdir('tests')
endif
