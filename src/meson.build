pkg = import('pkgconfig')
thread_dep = dependency('threads')
m_dep = cc.find_library('m', required : false)

inc = include_directories(
  '..',
  '../include',
  '../libcnary/include',
)

libplist = library('plist-2.0',
  'base64.c',
  'bytearray.c',
  'hashtable.c',
  'ptrarray.c',
  'time64.c',
  'xplist.c',
  'bplist.c',
  'plist.c',
  include_directories : inc,
  dependencies : [ thread_dep, m_dep ],
  link_with : libcnary,
  install : true,
)

pkg.generate(
  libraries : libplist,
  version: meson.project_version(),
  name : 'libplist-2.0',
  description : 'A library to handle Apple Property Lists whereas they are binary or XML',
)

if get_option('plistpp')
  libplistpp = library('plist++-2.0',
    'Node.cpp',
    'Structure.cpp',
    'Array.cpp',
    'Boolean.cpp',
    'Data.cpp',
    'Date.cpp',
    'Dictionary.cpp',
    'Integer.cpp',
    'Key.cpp',
    'Real.cpp',
    'String.cpp',
    'Uid.cpp',
    include_directories : inc,
    link_with : libplist,
    install : true,
  )

  pkg.generate(
    libraries : libplistpp,
    version: meson.project_version(),
    name : 'libplist++-2.0',
    description : 'C++ binding for libplist',
  )
endif
