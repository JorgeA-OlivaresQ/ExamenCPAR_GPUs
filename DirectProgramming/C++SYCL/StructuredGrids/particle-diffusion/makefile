# Makefile for NMAKE

default: run_all

all: run_all

run_all: motionsim.exe
	.\motionsim

SYCL_OPTS=/I"$(MKLROOT)\include" /Qmkl /DMKL_ILP64 /EHsc -fsycl-device-code-split=per_kernel -fno-sycl-early-optimizations OpenCL.lib

motionsim.exe: src\motionsim.hpp src\motionsim.cpp src\motionsim_kernel.cpp src\utils.cpp
	icx-cl -fsycl src\motionsim.cpp src\utils.cpp src\motionsim_kernel.cpp /Femotionsim.exe $(SYCL_OPTS)

clean:
	del /q motionsim.exe

pseudo: run_all clean all
