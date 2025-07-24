# Makefile for CUDA Image Enhancement Project

# Compiler
NVCC := /usr/local/cuda/bin/nvcc

# Compiler flags
# -O3 for optimization
# -arch=sm_35 specifies the target GPU architecture. Change sm_35 if you have a different GPU.
#   You can find your GPU's compute capability here: https://developer.nvidia.com/cuda-gpus
# -rdc=true enables relocatable device code, necessary for linking separate .cu files.
NVCC_FLAGS := -O3 -rdc=true -arch=sm_35

# C++ Compiler for host code (can be g++)
CXX := g++
CXX_FLAGS := -O3

# Executable name
TARGET := image_enhancer

# Source files
CU_SOURCES := image_processing.cu
CPP_SOURCES := main.cpp

# Object files
# Creates a corresponding .o file for each source file
CU_OBJS := $(CU_SOURCES:.cu=.o)
CPP_OBJS := $(CPP_SOURCES:.cpp=.o)
OBJS := $(CU_OBJS) $(CPP_OBJS)

# Include directories
# Add path to CUDA include files
INCLUDES := -I/usr/local/cuda/include

# Library directories and libraries
# Add path to CUDA libraries and specify libraries to link
# Add OpenCV libraries using pkg-config for portability
LDFLAGS := -L/usr/local/cuda/lib64 -lcudart
LDFLAGS += $(shell pkg-config --libs opencv4)

# Default target: build the executable
all: $(TARGET)

# Rule to link the final executable
$(TARGET): $(OBJS)
	@echo "Linking..."
	$(NVCC) $(NVCC_FLAGS) -o $(TARGET) $(OBJS) $(LDFLAGS)
	@echo "Build complete. Executable: $(TARGET)"

# Rule to compile CUDA source files (.cu) into object files (.o)
%.o: %.cu
	@echo "Compiling CUDA source: $<"
	$(NVCC) $(NVCC_FLAGS) $(INCLUDES) -c $< -o $@

# Rule to compile C++ source files (.cpp) into object files (.o)
%.o: %.cpp
	@echo "Compiling C++ source: $<"
	$(CXX) $(CXX_FLAGS) $(shell pkg-config --cflags opencv4) $(INCLUDES) -c $< -o $@

# Clean up build files
clean:
	@echo "Cleaning up..."
	rm -f $(OBJS) $(TARGET)
	@echo "Cleanup complete."

# Phony targets
.PHONY: all clean
