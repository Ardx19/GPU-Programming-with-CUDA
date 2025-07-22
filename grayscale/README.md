High-Performance Batch Image Grayscaling via CUDAAbstractThis project presents a high-performance application for the batch conversion of color images to grayscale, leveraging the parallel computing architecture of NVIDIA's CUDA platform. The program is engineered to systematically process a collection of images located within a designated input directory, utilizing GPU acceleration to perform the computationally intensive conversion tasks. The resulting grayscale images are subsequently stored in a specified output directory. This implementation serves as a practical demonstration of GPU-accelerated image processing, conforming to the structural requirements of the course project template.System RequirementsSuccessful compilation and execution of this software are contingent upon the following system components:NVIDIA GPU: The host system must be equipped with a CUDA-capable NVIDIA graphics processing unit.NVIDIA CUDA Toolkit: A complete installation of the NVIDIA CUDA Toolkit is required to provide the necessary nvcc compiler and associated development libraries.stb Image Libraries: The project's image I/O operations depend on the stb_image.h and stb_image_write.h single-file C/C++ libraries.Directory and File ArchitectureThe project adheres to the following directory structure to ensure modularity and clarity:/
|-- Makefile              # Facilitates the automated compilation of the project.
|-- src/                  # Contains all source code and header files.
|   |-- main.cu
|   |-- grayscale.cuh
|   |-- grayscale.cu
|   |-- stb_image.h           # Dependency: To be acquired by the user.
|   |-- stb_image_write.h     # Dependency: To be acquired by the user.
|-- input_data/           # Designated directory for source color images.
|-- output_data/          # Designated directory for generated grayscale images.
|-- results/              # Contains documentation verifying program execution.
    |-- proof.md
Installation and Operational Procedure
Step 1: Acquisition of DependenciesThe stb libraries are a prerequisite for this project. The following two files must be acquired from the official stb repository on GitHub and placed within the src/ directory:stb_image.hstb_image_write.h
Step 2: Data IngestionThe source images intended for conversion must be placed within the input_data/ directory.
Step 3: CompilationTo compile the source code, open a command-line terminal in the project's root directory and execute the make utility. This command invokes the nvcc compiler to build the source files and generate an executable file named grayscale_converter.make
Step 4: ExecutionThe program can be initiated by running the compiled executable from the terminal:./grayscale_converter
Upon execution, the application will process all image files located in the input_data/ directory. The corresponding grayscale output files will be written to the output_data/ directory.
Step 5: CleanupTo remove all intermediate object files and the final executable generated during the compilation process, the following command may be used:make clean
