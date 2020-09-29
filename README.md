# Docker image for C++/Python software development with OpenCV/CUDA

* Based on nvidia-docker2 image Ubuntu 16.04 / CUDA 9.1 / cuDNN 7
* Adds CMake 3.10.2 to use improved CUDA CMake integration
* Adds miniconda with two environments to build Python 2.7 and 3.6 OpenCV bindings
* Leverages conda to pull Intel MKL headers and shared libraries
* Adds Eigen 3.3.5 
* Adds TBB
* Builds OpenCV with all the above (OpenCV cmake generation downloads several other packages like Intel IPP)
* Builds cv2 python module without CUDA and without Intel MKL to make wheel file slightly more portable (many apt-get package still required)

OpenCV is installed in /opt/opencv-3.4.0

Example:

```
nvidia-docker run --rm -ti mlamarre/docker-cuda-opencv:latest /bin/bash
/# source activate ocvpy3
(ocvpy3) /# python
>>> import cv2
```

To call Python scripts using cv2 inside follow this example:
```
/bin/bash -c "source /opt/conda/envs/ocvpy3/bin/activate ocvpy3 && python setup.py install --yes USE_AVX_INSTRUCTIONS"\
```

This activates the conda environment with the installed cv2.pyd and runs python from that conda env.

The example above runs a setup.py for another project (took this from a docker building dlib). You can build your own environment using `pip install [wheel file]`. The setuptools wheel files are installed in `/usr/local/etc/wheels` 
