# Anexos

## DeviceQuery

### GPUS

Equipos en partición gpus \"Tesla K20\", salida de DeviceQuery:

| <!----> | <!----> | 
|---------|---------|
| Device 0: | \"Tesla K20m\" |
| CUDA Driver Version / Runtime Version | 10.2 / 9.0 |
| CUDA Capability Major/Minor version number: | 3.5 |
| **Total amount of global memory:** | **4744 MBytes (4974313472 bytes)** |
| **(13) Multiprocessors, (192) CUDA Cores/MP:** | **2496 CUDA Cores** |
| GPU Max Clock rate: | 706 MHz (0.71 GHz) |
| Memory Clock rate: | 2600 Mhz |
| Memory Bus Width: | 320-bit |
| L2 Cache Size: | 1310720 bytes |
| Maximum Texture Dimension Size (x,y,z) | 1D=(65536), 2D=(65536, 65536), 3D=(4096, 4096, 4096) |
| Maximum Layered 1D Texture Size, (num) layers | 1D=(16384), 2048 layers |
| Maximum Layered 2D Texture Size, (num) layers | 2D=(16384, 16384), 2048 layers |
| **Total amount of constant memory:** | **65536 bytes** |
| **Total amount of shared memory per block:** | **49152 bytes** |
| **Total number of registers available per block:** | **65536** |
| **Warp size:** | **32** |
| **Maximum number of threads per multiprocessor:** | **2048** |
| **Maximum number of threads per block:** | **1024** |
| **Max dimension size of a thread block (x,y,z):** | **(1024, 1024, 64)** |
| **Max dimension size of a grid size (x,y,z):** | **(2147483647, 65535, 65535)** |
| Maximum memory pitch: | 2147483647 bytes |
| Texture alignment: | 512 bytes |
| Concurrent copy and kernel execution: | Yes with 2 copy engine(s) |
| Run time limit on kernels: | No |
| Integrated GPU sharing Host Memory: | No |
| Support host page-locked memory mapping: | Yes |
| Alignment requirement for Surfaces: | Yes |
| Device has ECC support: | Enabled 
| Device supports Unified Addressing (UVA): | Yes |
| Device PCI Domain ID / Bus ID / location ID: | 0 / 12 / 0 |
| Compute Mode: | < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) > |

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 10.2, CUDA
Runtime Version = 9.0, NumDevs = 1, Device0 = Tesla K20m Result = PASS

### VGPUS

Equipos en partición vgpus "V100", salida de DeviceQuery:

| <!----> | <!----> | 
|---------|---------|
| Device 0: | "Tesla V100-SXM2-16GB" |
| CUDA Driver Version / Runtime Version | 10.2 / 9.0 |
| CUDA Capability Major/Minor version number: | 7.0 |
| **Total amount of global memory:** | **16160 MBytes (16945512448 bytes)** |
| **(80) Multiprocessors, ( 64) CUDA Cores/MP:** | **5120 CUDA Cores** |
| GPU Max Clock rate: | 1530 MHz (1.53 GHz) |
| Memory Clock rate: | 877 Mhz |
| Memory Bus Width: | 4096-bit |
| L2 Cache Size: | 6291456 bytes |
| Maximum Texture Dimension Size (x,y,z) | 1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384) |
| Maximum Layered 1D Texture Size, (num) layers | 1D=(32768), 2048 layers |
| Maximum Layered 2D Texture Size, (num) layers | 2D=(32768, 32768), 2048 layers |
| **Total amount of constant memory:** | **65536 bytes** |
| **Total amount of shared memory per block:**  | **49152 bytes** |
| **Total number of registers available per block:** | **65536** |
| **Warp size:** | **32** |
| **Maximum number of threads per multiprocessor:** | **2048** |
| **Maximum number of threads per block:** | **1024** |
| **Max dimension size of a thread block (x,y,z):** | **(1024, 1024, 64)** |
| **Max dimension size of a grid size (x,y,z):** | **(2147483647, 65535, 65535)** |
| Maximum memory pitch: | 2147483647 bytes |
| Texture alignment: | 512 bytes |
| Concurrent copy and kernel execution: | Yes with 3 copy engine(s) |
| Run time limit on kernels: | No |
| Integrated GPU sharing Host Memory: | No |
| Support host page-locked memory mapping: | Yes |
| Alignment requirement for Surfaces: | Yes |
| Device has ECC support: | Enabled |
| Device supports Unified Addressing (UVA): | Yes |
| Device PCI Domain ID / Bus ID / location ID: | 0 / 98 / 0 |
| Compute Mode: | < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) > |

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 10.2, CUDA
Runtime Version = 9.0, NumDevs = 1, Device0 = Tesla V100-SXM2-16GB
Result = PASS

