# emscripten lto testing

## env

```
$ em++ --version
emcc (Emscripten gcc/clang-like replacement) 1.36.3 (commit 3ac90308b3c77d1fcbb71fe0bdd465aa5003c00e)
Copyright (C) 2014 the Emscripten authors (see AUTHORS.txt)
This is free and open source software under the MIT license.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

```
$ clang --version
clang version 3.9.0 (https://github.com/kripken/emscripten-fastcomp-clang/ ebce0a585917af1f69cc372c3730a709ea97dc8c) (https://github.com/kripken/emscripten-fastcomp/ 8f1637cd5980ed8172b3874b6fdbd2f7829f92ed) (emscripten 1.36.3 : 1.36.3)
Target: i686-pc-linux-gnu
Thread model: posix
InstalledDir: /home/legokichi/emsdk_portable/clang/fastcomp/build_incoming_32/bin
```

```
$ ./firefox --version
Mozilla Firefox 49.0a1
```

```
-rw-rw-r-- 1 legokichi legokichi 1149088  5月  8 21:54 libsatori.default.js
-rw-rw-r-- 1 legokichi legokichi 2202632  5月  8 22:11 libsatori.lto.js
```

## default

```
CXXFLAGS = -O3 -Wall -std=c++11 -s ALLOW_MEMORY_GROWTH=1
LDFLAGS = -O3 -shared --memory-init-file 0 --pre-js em-pre.js --post-js em-post.js -s EXPORTED_FUNCTIONS=$(EXPORTED_FUNCTIONS) -s ALLOW_MEMORY_GROWTH=1
```

![](https://i.gyazo.com/28072e0ae727466bb02a504980746b31.png)

## LTO

```
CXXFLAGS = -O3 -Wall -std=c++11
LDFLAGS = -O3 --llvm-lto 2 --closure 1 --memory-init-file 0 --pre-js em-pre.js --post-js em-post.js -s EXPORTED_FUNCTIONS=$(EXPORTED_FUNCTIONS)
```

![](https://i.gyazo.com/d6afc204e5b28122b76b017f1ea14efa.png)


## reference

* https://kripken.github.io/emscripten-site/docs/optimizing/Optimizing-Code.html
* https://kripken.github.io/emscripten-site/docs/tools_reference/emcc.html
