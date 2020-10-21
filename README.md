# Robotics with GPU computing

Cupoch is a library that implements rapid 3D data processing and robotics computation using CUDA.

The goal of this library is to process the input of 3D sensors rapidly and use it to control the robot. This library is based on the functionality of Open3D, with additional features for integration into robot systems.

## Core Features
* 3D data processing and robotics computation using CUDA
	* Point cloud registration (ICP, ColoredICP)
	* Point cloud clustering
		* G-DBSCAN: A GPU Accelerated Algorithm for Density-based Clustering
	* Point cloud/Triangle mesh filtering, down sampling
	* Visual Odometry
		* Real-time visual odometry from dense RGB-D images
		* Robust Odometry Estimation for RGB-D Cameras
	* Collision checking
	* Occupancy grid
	* Distance transform
		* Parallel Banding Algorithm to Compute Exact Distance Transform with the GPU
	* Path finding on graph structure
	* Path planning for collision avoidance
* Open3D-like API
* Support memory pool and managed allocators
* Interactive GUI (OpenGL CUDA interop and imgui)
* Interoperability between cupoch 3D data and DLPack(Pytorch, Cupy,...) data structure

## Installation
This software is tested under 64 Bit Ubuntu Linux 18.04 and CUDA 10.0/10.1/10.2. You can install cupoch using pip.

```
pip install cupoch
```

Or install cupoch from source.

```
git clone https://github.com/neka-nat/cupoch.git --recurse
cd cupoch
mkdir build
cd build
cmake ..; make install-pip-package -j
```

### Installation for Jetson
You can also install cupoch using pip on Jetson. Please set up Jetson using jetcard and install some packages with apt.

```
sudo apt-get install libxinerama-dev libxcursor-dev libglu1-mesa-dev
pip3 install https://github.com/neka-nat/cupoch/releases/download/v0.0.9/cupoch-0.0.9.0-cp36-cp36m-linux_aarch64.whl
```

## Results
The figure shows Cupoch's point cloud algorithms speedup over Open3D. The environment tested on has the following specs:

* Intel Core i7-7700HQ CPU
* Nvidia GTX1070 GPU
* OMP_NUM_THREAD=1

You can get the result by running the example script in your environment.

```
cd examples/python/basic
python benchmarks.py
```

## References
* CUDA repository forked from Open3D, https://github.com/theNded/Open3D
* GPU computing in Robotics, https://github.com/JanuszBedkowski/gpu_computing_in_robotics
* Voxel collision comupation for robotics, https://github.com/fzi-forschungszentrum-informatik/gpu-voxels