
High-Performance Batch Image Grayscaling via CUDA
==================================================

Abstract
--------
This project presents a high-performance application for the batch conversion of color images to grayscale, leveraging the parallel computing architecture of NVIDIA's CUDA platform. The program is engineered to systematically process a collection of images located within a designated input directory, utilizing GPU acceleration to perform the computationally intensive conversion tasks. The resulting grayscale images are subsequently stored in a specified output directory. This implementation serves as a practical demonstration of GPU-accelerated image processing, conforming to the structural requirements of the course project template.

System Requirements
-------------------
Successful compilation and execution of this software are contingent upon the following system components:

- NVIDIA GPU: The host system must be equipped with a CUDA-capable NVIDIA graphics processing unit.
- NVIDIA CUDA Toolkit: A complete installation of the NVIDIA CUDA Toolkit is required to provide the necessary `nvcc` compiler and associated development libraries.
- stb Image Libraries: The project's image I/O operations depend on the `stb_image.h` and `stb_image_write.h` single-file C/C++ libraries.

Directory and File Architecture
-------------------------------
The project adheres to the following directory structure to ensure modularity and clarity:

/
|-- Makefile               # Facilitates the automated compilation of the project.
|-- src/                   # Contains all source code and header files.
|   |-- main.cu
|   |-- grayscale.cuh
|   |-- grayscale.cu
|   |-- stb_image.h        # Dependency: To be acquired by the user.
|   |-- stb_image_write.h  # Dependency: To be acquired by the user.
|-- input_data/            # Designated directory for source color images.
|-- output_data/           # Designated directory for generated grayscale images.
|-- results/               # Contains documentation verifying program execution.
|   |-- proof.md

Installation and Operational Procedure
--------------------------------------

Step 1: Acquisition of Dependencies
-----------------------------------
The stb libraries are a prerequisite for this project. The following two files must be acquired from the official stb repository on GitHub and placed within the `src/` directory:

- stb_image.h
- stb_image_write.h

Repository: https://github.com/nothings/stb

Step 2: Data Ingestion
----------------------
Place all the source images intended for conversion within the `input_data/` directory.

Step 3: Compilation
-------------------
To compile the source code, open a terminal in the project root and run:

    make

This will invoke `nvcc` to build the project and create an executable named `grayscale_converter`.

Step 4: Execution
-----------------
To run the program:

    ./grayscale_converter

The application will process all image files found in the `input_data/` directory. The corresponding grayscale images will be written to `output_data/`.

Step 5: Cleanup
---------------
To remove intermediate object files and the compiled executable:

    make clean
