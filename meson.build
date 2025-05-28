# https://mesonbuild.com/
project(
    'my-fantastic-simulation-code', # Project name
    ['c', 'cpp'], # Project type. We need a C++ compiler. The C compiler is required for MPI.
    default_options : ['cpp_std=c++17'], # Yes, we need C++17, at least for constexpr
    version : '0.1'
)

# Optional dependency: Eigen3 linar algebra library
# Make sure to add 'eigen' to the dependencies in your subdirectories if you
# enable this.
# eigen = dependency('eigen3', version: '>=3.4.0')

# Optional dependency: Kokkos C++ performance portability library
# Make sure to add 'kokkoscore' to the dependencies in your subdirectories if you
# enable this.
# cmake = import('cmake')
# kokkos_options = cmake.subproject_options()
# kokkos_options.add_cmake_defines({
#   'Kokkos_ENABLE_SERIAL': true, # Serial execution
#   'Kokkos_ENABLE_THREADS': true, # Threads
#   'Kokkos_ENABLE_OPENMP': false, # OpenMP support
#   'Kokkos_ENABLE_CUDA': false, # CUDA support
#   'Kokkos_ENABLE_HIP': false, # HIP support
# })
# kokkos = cmake.subproject('kokkos', options: kokkos_options)
# kokkoscore = kokkos.dependency('kokkoscore')

# Detect MPI, but make it optional
mpi = dependency('mpi', language: 'cpp', required: false)

if mpi.found()
    add_project_arguments('-DWITH_MPI', language : ['c', 'cpp'])
    message('MPI found')
else
    message('MPI not found, disabling MPI support')
endif

subdir('src')
subdir('executables')
subdir('tests')