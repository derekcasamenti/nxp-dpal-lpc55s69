project('nxp-dpal-lpc55s69', 'c',
    license : 'BSD-3-Clause',
    version : '1.1',
    default_options : [
        'warning_level=2',
    ],
)

cpu_core = get_option('cpu_core')

if cpu_core == 'CORE_0'
    defines = '-DCPU_LPC55S69JBD100_cm33_core0'
    src = 'src/system_LPC55S69_cm33_core0.c'
else
    defines = '-DCPU_LPC55S69JBD100_cm33_core1'
    src = 'src/system_LPC55S69_cm33_core1.c'
endif
add_project_arguments(defines, language : 'c')

inc = include_directories('include', is_system : true)

cmsis_core_m_proj = subproject('cmsis-core-m')
cmsis_core_m_dep = cmsis_core_m_proj.get_variable('cmsis_core_m_dep')

nxp_dpal_lpc55s69_lib = static_library('nxp-dpal-lpc55s69', src,
    include_directories : inc,
    dependencies : cmsis_core_m_dep,
    implicit_include_directories: false,
    pic: false,
)

nxp_dpal_lpc55s69_dep = declare_dependency(
    include_directories : inc,
    link_with : nxp_dpal_lpc55s69_lib,
    variables : {'cpu_core': cpu_core}
)
