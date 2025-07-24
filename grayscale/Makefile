# Makefile for CUDA Grayscale Converter

# Compiler
NVCC = nvcc

# Compiler flags
# -O3 for optimization
# -arch=sm_35 for compute capability 3.5 (Kepler), a common baseline.
# Adjust -arch as needed for your specific GPU.
NVCC_FLAGS = -O3 -arch=sm_35

# Executable name
EXE = grayscale_converter

# Source files
SRCS = src/main.cu src/grayscale.cu

# Object files
OBJS = $(SRCS:.cu=.o)

# Default target
all: $(EXE)

# Link object files to create the executable
$(EXE): $(OBJS)
	$(NVCC) $(NVCC_FLAGS) -o $@ $^

# Compile .cu source files into .o object files
%.o: %.cu
	$(NVCC) $(NVCC_FLAGS) -c -o $@ $<

# Clean up build files
clean:
	rm -f $(EXE) $(OBJS)
