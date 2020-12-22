project('libplist', 'c', 'cpp',
  version : '2.2.1',
  default_options : [ 'c_std=gnu11', 'cpp_std=c++98' ])

cc = meson.get_compiler('c')
cdata = configuration_data()

cdata.set_quoted('PACKAGE_NAME', meson.project_name())
cdata.set_quoted('PACKAGE_VERSION', meson.project_version())
cdata.set_quoted('PACKAGE_URL', 'https://libimobiledevice.org')
cdata.set_quoted('PACKAGE_BUGREPORT', 'https://libimobiledevice.org')

cdata.set('HAVE_DLFCN_H', cc.has_header('dlfcn.h'))
cdata.set('HAVE_INTTYPES_H', cc.has_header('inttypes.h'))
cdata.set('HAVE_MEMORY_H', cc.has_header('memory.h'))
cdata.set('HAVE_STDINT_H', cc.has_header('stdint.h'))
cdata.set('HAVE_STDLIB_H', cc.has_header('stdlib.h'))
cdata.set('HAVE_STRINGS_H', cc.has_header('strings.h'))
cdata.set('HAVE_STRING_H', cc.has_header('string.h'))
cdata.set('HAVE_SYS_STAT_H', cc.has_header('sys/stat.h'))
cdata.set('HAVE_SYS_TYPES_H', cc.has_header('sys/types.h'))
cdata.set('HAVE_UNISTD_H', cc.has_header('unistd.h'))

cdata.set('HAVE_ASPRINTF', cc.has_function('asprintf', prefix: '#define _GNU_SOURCE\n#include <stdio.h>'))
cdata.set('HAVE_GMTIME_R', cc.has_function('gmtime_r', prefix: '#include <time.h>'))
cdata.set('HAVE_LOCALTIME_R', cc.has_function('localtime_r', prefix: '#include <time.h>'))
cdata.set('HAVE_MEMMEM', cc.has_function('memmem', prefix: '#define _GNU_SOURCE\n#include <string.h>'))
cdata.set('HAVE_STPCPY', cc.has_function('stpcpy', prefix: '#include <string.h>'))
cdata.set('HAVE_STRCASECMP', cc.has_function('strcasecmp', prefix: '#include <strings.h>'))
cdata.set('HAVE_STRDUP', cc.has_function('strdup', prefix: '#include <string.h>'))
cdata.set('HAVE_STRERROR', cc.has_function('strerror', prefix: '#include <string.h>'))
cdata.set('HAVE_STRNDUP', cc.has_function('strndup', prefix: '#include <string.h>'))
cdata.set('HAVE_STRPTIME', cc.has_function('strptime', prefix: '#define _XOPEN_SOURCE\n#include <time.h>'))
cdata.set('HAVE_TIMEGM', cc.has_function('timegm', prefix: '#include <time.h>'))
cdata.set('HAVE_VASPRINTF', cc.has_function('vasprintf', prefix: '#define _GNU_SOURCE\n#include <stdio.h>'))

cdata.set('HAVE_TM_TM_GMTOFF', cc.has_member('struct tm', 'tm_gmtoff', prefix: '#include <time.h>'))
cdata.set('HAVE_TM_TM_ZONE', cc.has_member('struct tm', 'tm_zone', prefix: '#include <time.h>'))

if target_machine.endian() == 'big'
  cdata.set('__BIG_ENDIAN__', 1)
else
  cdata.set('__LITTLE_ENDIAN__', 1)
endif

configure_file(input : 'config.h.meson',
  output : 'config.h',
  configuration : cdata)

libplist_incdir = include_directories('include')

add_global_arguments('-DHAVE_CONFIG_H', language : 'c')

install_headers('include/plist/plist.h', subdir : 'plist')
if get_option('plistpp')
  install_headers(
    'include/plist/Array.h',
    'include/plist/Boolean.h',
    'include/plist/Data.h',
    'include/plist/Date.h',
    'include/plist/Dictionary.h',
    'include/plist/Integer.h',
    'include/plist/Key.h',
    'include/plist/Node.h',
    'include/plist/plist++.h',
    'include/plist/Real.h',
    'include/plist/String.h',
    'include/plist/Structure.h',
    'include/plist/Uid.h',
    subdir : 'plist',
  )
endif

subdir('libcnary')
subdir('src')
subdir('tools')
