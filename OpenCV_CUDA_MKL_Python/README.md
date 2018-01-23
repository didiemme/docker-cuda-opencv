# Docker image for C++/Python software development with OpenCV/CUDA

* Based on nvidia-docker2 image Ubuntu 16.04 / CUDA 9.1 / cuDNN 7
* Adds CMake 3.10.2 to use improved CUDA CMake integration
* Adds miniconda with two environments to build Python 2.7 and 3.6 OpenCV bindings
* Leverages conda to pull Intel MKL headers and shared libraries
* Adds Eigen 3.3.4 
* Adds TBB
* Builds OpenCV with all the above (OpenCV cmake generation downloads several other packages like Intel IPP)