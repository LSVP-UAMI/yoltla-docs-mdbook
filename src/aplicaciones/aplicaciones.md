# Aplicaciones

Las aplicaciones en el clúster Yoltla están disponibles mediante la 
herramienta *Modules*. Esta herramienta permite crear, modificar y 
agregar valores a las variables de entorno necesarias para el 
funcionamiento de las aplicaciones instaladas en Yoltla, además facilita
 la ejecución, compilación y uso de múltiples versiones de aplicaciones.

*Modules* está disponible para todos los usuarios a través del comando `module`. 
Por ejemplo, para hacer uso de los compiladores y herramientas de intel, 
ejecute el comando:
```
[pepe@yoltla0 ~]$ module load intel/compilers-2017u4
```

Para obtener más información acerca de las aplicaciones disponibles en el 
clúster y su uso, consulte la sección [¿Cómo utilizo las aplicaciones del clúster?.](../tutoriales/aplicaciones_del_cluster.md)

## Software disponible

### Compiladores

| **Compiladores/<br>Interpretes** | <!----> | **Versiones** | <!----> | <!----> |
|----------------------------------|---------|---------------|---------|---------|
| cuda | 5.0 | 5.5 | 6.0 | 6.5 |
| cuda | 7.0 | 7.5 | 8.0 | 9.0 |
|cuda | 10.2 | 
| gcc | 5.4.0 | 5.5.0 |6.4.0 |7.2.0 |
| gcc | 8.5.0 | 9.5.0 |10.4.0 |11.3.0 |
| gcc | 12.1.0 |
| intel compilers | 15.2.164 | 15.6.232 | 16.3.210 | 2017u4 |
|intel-oneapi-compilers |2022.2.1 |
| jdk | 1.7.0_17 |1.8 |
| python | 2.7.11 | 3.5.1 | 3.8.7_extra-packages |
| python | 3.12 | 3.8.12 | 3.8.12_scikit-learn-1.0.1 |3.8.7 |
| python-conda | 2.7 | 3.6 |
| python-intel | 2.7 |
| R | 4.0.2 | 

### MPIs

| **MPIs** | <!----> | **Versiones** | <!----> | <!----> |
|----------|---------|---------------|---------|---------|
| openmpi |1.8.4 | 2.0.2 | 2.1.5 | 3.1.4 |
| hpcx-mpi | 2.13 |
| intel impi | 5.0.3.048 | 5.0.3.49 | 5.1.3 | 2017u4 |
| intel-oneapi-mpi | 2021.7.1 |

### Aplicaciones

| **Aplicaciones** | <!----> | **Versiones** | <!----> | <!----> |
|------------------|---------|---------------|---------|---------|
| abinit | 8.4.1 | 9.6.2 |
| amber | ambertools19 |
| anaconda | 2021.04 | 2023.03 |
| aocc | 3.2.0 |
| aocl | amdblis-3.2 | amdfftw-3.2 | amdlibflame-3.2 | amdscalapack-3.2 |
| aocl | tools-3.2 |
| autodock-vina | 1.2.5 |
| gaussian | 09 | 09-sse4 |
| fftw | 2.1.5 | 3.3.4 |
| espresso | 5.0.2 | 5.4.0 |
| gpaw | 1.0.0 |
| gromacs | 4.5_d | 4.6.7 | 5.0.7-d | 5.0.7-s |
| gromacs | 5.1.4-s | 2016.3 | 2016.5 | 2018 |
| gromacs | 2019.2 | 5.1.5-CUDA | 2022.3 |
| nwchem | 6.3 | 6.6 | 6.8 | 7.0.2 |
| nwchem | 7.0.2_zen3 |
| onetep | 3.0.0-y1 |
| vasp | 5.3-y1 | 5.4.1-y1 | 5.4.4 | 6.4.1 |
| vasp | 6.4.1-libxc-6.2.2 | 6.4.2-libxc-6.2.2 | 6.3.2 | 6.3.2_libxc |
| vasp | 6.3.2_libxc_scalapack | 6.4.1_wannier90
| namd | 2.11 | 2.12 | 2.12-CUDA | 2.12-GIT-CUDA
| namd | 2.13 | 2.13-CUDA |
| grace | 5.99.0 |
| hdf5 | 1.8.17 | 1.8.17-y1 |
| netcdf | 4.4.1 |
| octave | 4.0.3 | 8.2.0 |
| openblas | 0.2.19 |
| szip | 2.1 |
| mathematica | 10.2 | 11.2 |
| libevent | 2.0.22 |
| tmux | 2.0 | 3.2a |
| vmd | 1.9.2 |
| binutils | 2.32 |
| carma | 2.01 |
| charmm | 44b1 | 44b1_repdstr |
| cmake | 3.23 |
| crystal | 14 | 17 | 23 |
| curl | 7.83.0 |
| dftb+ | 18.1 | 18.2 |
| dl_poly_classic | 1.10 |
| elk | 7.2.42 |
| gamess_us | 2020.2 |
| git | 2.22 |
| g_mmpbsa | 1.6 |
| golang | 1.11.1 |
| gomc | 2.11 | 2.31 | 2.40 | 2.60 |
| gomc | 2.70 |
| hoomd | 2.9.7 |
| hwloc | 2.7.1 |
| jdftx | 1.7.0_cpu | 1.7.0_gpu | 1.3.1 |
| lammps | 2018-05-Imp_mpi-gpu | 2018-12-lmp-cpu | 2019-08-Imp-gpu | 2020-10-Imp-gpu |
| lammps | 2021-10-Imp-cpu | 2021-05-Imp-cpu | 11092016 |
| likwid | 4.3.3 |
| matlab | r2020a |
| openbabel | 2.2.3 |
| openmm | 7.4.1 |
| openssl | 1.1.1.i | 1.1.1o | 3.0.0 |
| orca | 3.0.3 | 4.0.0.2 | 4.0.1.2 | 4.2.0 |
| physicell | x-1.11.0 |
| plumed | 2.4-mpi | 2.4-serial |
| plumed+gromacs | 2016.5 | 2016.5-gpu | 2018.1 | 2018.1-gpu |
| py-gpaw | 21.1.0 |
| quantum-espresso | 6.2.1 | 6.4.1 |
| samtools | 1.10 |
| scuff-em | git-9c6d0cb |
| siesta | 4.0.1 | 4.1-b4 | master_4.1-262 | trunk-462 |
| singularity-evolinc-i | 5.0 |
| singularity-evolinc-ii | 5.0 |
| singularity-hoomd | 2.3.5-CUDA |
| trimmomatic | 0.39 |
| turbogap | git-f3afb8c |
| vim | 8.1 |
| wannier90 | 3.1.0
| wien2k | 19.1 | 21.1 |
| xtb | 6.2.3 |
| yasara | 22.9.24 |
| intel xe | 13.2.144 |
| intel mkl | 15.2.164 | 15.6.232 | 16.3.210 | 2017u4 |
| intel-oneapi-mkl | 2022.2.1 |
| intel-oneapi-tbb | 2021.7.1 |