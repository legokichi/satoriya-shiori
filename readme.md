# emscripten lto testing


## default
```
CXXFLAGS = -O3 -Wall -std=c++11 -s ALLOW_MEMORY_GROWTH=1
LDFLAGS = -O3 -shared --memory-init-file 0 --pre-js em-pre.js --post-js em-post.js -s EXPORTED_FUNCTIONS=$(EXPORTED_FUNCTIONS) -s ALLOW_MEMORY_GROWTH=1
```

![](https://i.gyazo.com/28072e0ae727466bb02a504980746b31.png)

## LTO

```
CXXFLAGS = -O3 -Wall -std=c++11^M
LDFLAGS = -O3 --llvm-lto 2 --closure 1 --memory-init-file 0 --pre-js em-pre.js --post-js em-post.js -s EXPORTED_FUNCTIONS=$(EXPORTED_FUNCTIONS)
```

![](https://i.gyazo.com/d6afc204e5b28122b76b017f1ea14efa.png)


## reference

* https://kripken.github.io/emscripten-site/docs/optimizing/Optimizing-Code.html
* https://kripken.github.io/emscripten-site/docs/tools_reference/emcc.html
