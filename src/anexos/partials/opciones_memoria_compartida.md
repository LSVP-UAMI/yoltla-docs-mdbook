
|       | **GNU** | **Intel Suite** |
|-------|---------|-----------------|
| Compilador de lenguaje C | gcc | icc |
| Compilador de lenguaje C++ | g++ | icpc |
| Compilador de lenguaje Fortran | gfortran | ifort |
| Threads openmp | -fopenmp | -openmp |
| phreads | -pthread | -pthread |
| Optimización de código | -O0<br>-O1<br>-O2<br>-O3<br>-ffast-math | -O0<br>-O1<br>-O2<br>-O3<br>-fast |
| Reporte de mensajes de precaución en la compilación | -Wall | -Wall |
| Habilitar AVX | -mavx | -mavx |
| Habilitar AVX2<br>(solo para nodos tt) |  | -march=core-avx2<br><br>-axCORE-AVX512<br>-axCORE-AVX2<br>-axAVX |
