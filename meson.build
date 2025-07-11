project('config-parser', 'cpp', version : '23.11',
  default_options : [
  'cpp_std=c++20',
])

defines = []

if host_machine.system() == 'windows'
  defines += ['-DCONFIG_PLATFORM_WINDOWS']
else
  # Well... it could be something else.
  defines += ['-DCONFIG_PLATFORM_POSIX']
endif

fmt_dep = dependency('fmt')
doctest_dep = dependency('doctest')

src = ['src/config_parser/config_parser.hpp',
       'src/config_parser/config_parser.cc',
       'src/config_parser/config_parser_utils.hpp',
       'src/config_parser/config_parser_utils.cc',
       'src/config_parser/config_serializer.hpp',
       'src/config_parser/config_serializer.cc',
       'src/config_parser/config_tokenizer.hpp',
       'src/config_parser/config_tokenizer.cc',
]

src_test = [
  'src/config_parser/config_parser_tests.cc',
  'src/config_parser/config_serializer_tests.cc',
  'src/config_parser/config_tokenizer_tests.cc',
]

config_parser_dep = declare_dependency(
  sources: src,
  include_directories: include_directories([
    'src',
  ]),
  dependencies: [fmt_dep]
)

config_parser_test_dep = declare_dependency(
  sources: src_test,
  include_directories: include_directories([
    'src',
  ]),
  dependencies: [config_parser_dep, doctest_dep]
)
