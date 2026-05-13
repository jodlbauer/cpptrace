project('cpptrace', 'cpp')

flags = [
    '-DCPPTRACE_DEMANGLE_WITH_CXXABI',
    '-DCPPTRACE_UNWIND_WITH_NOTHING',
    '-DCPPTRACE_GET_SYMBOLS_WITH_LIBDL',
]

cpptrace_lib = library(
    'cpptrace',
    'src/unwind/unwind_with_libunwind.cpp',
    'src/unwind/unwind_with_winapi.cpp',
    'src/unwind/unwind_with_execinfo.cpp',
    'src/unwind/unwind_with_unwind.cpp',
    'src/unwind/unwind_with_dbghelp.cpp',
    'src/unwind/unwind_with_nothing.cpp',
    'src/symbols/symbols_with_libdwarf.cpp',
    'src/symbols/symbols_with_libbacktrace.cpp',
    'src/symbols/symbols_with_dbghelp.cpp',
    'src/symbols/symbols_core.cpp',
    'src/symbols/symbols_with_dl.cpp',
    'src/symbols/dwarf/dwarf_resolver.cpp',
    'src/symbols/dwarf/debug_map_resolver.cpp',
    'src/symbols/dwarf/dwarf_options.cpp',
    'src/symbols/symbols_with_addr2line.cpp',
    'src/symbols/symbols_with_nothing.cpp',
    'src/prune_symbol.cpp',
    'src/snippets/snippet.cpp',
    'src/logging.cpp',
    'src/utils/replace_all.cpp',
    'src/utils/io/memory_file_view.cpp',
    'src/utils/io/file.cpp',
    'src/utils/string_view.cpp',
    'src/utils/error.cpp',
    'src/utils/utils.cpp',
    'src/utils/microfmt.cpp',
    'src/cpptrace.cpp',
    'src/from_current.cpp',
    'src/utils.cpp',
    'src/jit/jit_objects.cpp',
    'src/exceptions.cpp',
    'src/ctrace.cpp',
    'src/binary/pe.cpp',
    'src/binary/elf.cpp',
    'src/binary/object.cpp',
    'src/binary/safe_dl.cpp',
    'src/binary/module_base.cpp',
    'src/binary/mach-o.cpp',
    'src/formatting.cpp',
    'src/platform/memory_mapping.cpp',
    'src/platform/dbghelp_utils.cpp',
    'src/options.cpp',
    'src/demangle/demangle_with_cxxabi.cpp',
    'src/demangle/demangle_with_winapi.cpp',
    'src/demangle/demangle_with_nothing.cpp',
    cpp_args : flags,
    include_directories : ['include', 'src'],
    build_by_default : true,
    install : true,
)

install_subdir(
    'include',
    strip_directory : true,
    install_dir : get_option('includedir'),
)

pkg = import('pkgconfig')
pkg.generate(cpptrace_lib, extra_cflags : flags)

cpptrace_dep = declare_dependency(
    include_directories : 'include',
    link_with : cpptrace_lib,
    compile_args : flags,
)
