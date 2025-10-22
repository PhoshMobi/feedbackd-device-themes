theme_json = [
  'google,bonito.json',
  'google,sargo.json',
  'oneplus,enchilada.json',
  'oneplus,fajita.json',
  'pine64,pinephone.json',
  'pine64,pinephone-pro.json',
  'purism,librem5.json',
  'samsung,midas.json',
  'shift,axolotl.json',
  'xiaomi,beryllium.json',
]

install_data(theme_json, install_dir: feedbackd_theme_dir)

if json_glib_validate.found()
  jsons = []
  foreach theme : theme_json
    jsons += (join_paths(meson.current_source_dir(), theme))
  endforeach
  custom_target(
    'validate-json',
    build_by_default: true,
    input: theme_json,
    output: 'json_validate_stamp',
    command: [json_glib_validate.path()] + jsons,
  )
endif

# Symlinks for non-mainline names when the user didn't do "fastboot erase dtbo"
install_symlink('google,b4s4-sdm670.json',
                install_dir: feedbackd_theme_dir,
                pointing_to: 'google,bonito.json')
