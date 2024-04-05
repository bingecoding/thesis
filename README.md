# Scalable Lighting for Global Illumination

Rendering each pixel in a scene with ray tracing can be done independently.
<br>
Path divergence for rays traced through a pixel, means that some pixels will take longer to render.
<br>
The most costly operation in physically based rendering is to determine if a ray has intersected an object.
<br>
<br>
The [Lightcuts](https://www.cs.cornell.edu/~kb/projects/lightcuts/) rendering technique reduces this cost by 
clustering [VPLs](https://dl.acm.org/doi/pdf/10.1145/258734.258769) in a preprocessing stage.
<br>
Focus of this thesis was to apply this method, to further reduce costs by running the computations in parallel.
<br>
[OpenCL](https://www.khronos.org/opencl/) provides a vendor neutral API, so that computations can be offloaded to CPUs and GPUs from Nvidia, AMD or Intel.
<br><br>
All scenes in the thesis were rendered with [dprt](https://github.com/bingecoding/dprt) and the Lightcuts method was ported 
to OpenCL ([see here](https://github.com/bingecoding/dprt/blob/main/src/kernels/lightcutsgpu_kernel.cl)).
<br>
Reconstruction Cuts is a more advanced variation of lightcuts that exploits spatial coherency to further reduce costs.
<br>
This method was first prototyped in C++ ([see here](https://github.com/bingecoding/dprt/blob/main/src/engines/reconstructioncutscpu.cpp)) 
and then ported to OpenCL ([see here](https://github.com/bingecoding/dprt/blob/main/src/kernels/reconstructioncutsgpu_kernel.cl)).