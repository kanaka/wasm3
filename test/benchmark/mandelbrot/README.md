# mandelbrot

Based on https://github.com/josch/mandelbrot

<img align="center" width="50%" src="image.png">

### Results

```log
TODO
```

### Building

```sh
wasicc -O3 -s mandel_dd.c -o mandel_dd.wasm
wasicc -O3 -s mandel.c -o mandel.wasm
```

### Running

```sh
export ENGINES_PATH=/opt/wasm_engines

# Wasm3
../../../build/wasm3 mandel_dd.wasm > image.ppm

# WAC
$ENGINES_PATH/wac/wax mandel_dd.wasm > image.ppm

# wasm-micro-runtime
$ENGINES_PATH/wasm-micro-runtime/core/iwasm/products/linux/build/iwasm mandel_dd.wasm > image.ppm

# wasmtime
wasmtime --optimize mandel_dd.wasm > image.ppm

# Wasmer
wasmer run mandel_dd.wasm > image.ppm
wasmer run --backend singlepass mandel_dd.wasm > image.ppm
wasmer run --backend llvm       mandel_dd.wasm > image.ppm

# Wasmer-JS (V8)
wasmer-js run mandel_dd.wasm > image.ppm

node --wasm_interpret_all $(which wasmer-js) run mandel_dd.wasm > image.ppm

# WAVM
$ENGINES_PATH/WAVM/Release/bin/wavm run mandel_dd.wasm > image.ppm
```