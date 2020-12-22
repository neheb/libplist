inc = include_directories(
  '../include',
  '..',
)

executable('plistutil',
  'plistutil.c',
    install: true,
    include_directories : [inc],
    link_with : libplist,
)
