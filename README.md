Cuda-Engined Adaptive Optics
==================================

CEO is a Linear Minimum Mean Square Error wavefront estimator for Shack--Hartmann wavefront sensor based Adaptive Optics systems.
CEO reconstructs the wavefront on-axis from one or several guide stars. The guide stars can be either Natural Guide Stars or Laser Guide Stars.
The wavefront estimator algorithm is written in CUDA 5.0 and it relies on CUFFT, CUBLAS and CUSPARSE.

Compiling CEO
-------------
The CEO library is compiled with `make all` and the PDF documentation is generated with `make doc`.
[noweb](http://www.cs.tufts.edu/~nr/noweb/) is required in order to generate the code and the documentation and Latex is needed to compile the documentation. 

Prior to compiling the library, you must set the `CEOPATH`, `CUDAPATH` and `NOWEBPATH` variables in `commom.mk` such as they match you local paths.
The library contains an atmosphere model with a number of turbulence layers that is set at compile time.
The number of layers is set by the variable `_N_LAYER_` in `include/definition.h`.
You have to change the value of `_N_LAYER` to match your atmosphere model.

CEO has some limited plotting capability using [plotly](http://plot.ly).
CEO has a wrapper for the REST API of plotly and it requires [libcurl](http://curl.haxx.se/libcurl/).
To use plotly, you need to sign in on [plotly](http://plot.ly) website and copy your username and key in `include/plotly.credentials`.
If you don't want to compile CEO with the plotly wrapper, you have to remove plotly from the `SOURCE_DIR` variables in `Makefile`.

Running the examples
--------------------
The example codes in the `TUTORIAL` directory are all compiled the same way, in the following we show how to compile and execute the `ngsao.nw` example:
```shell
cd TUTORIAL
make ngsao.bin
./a.out
```
