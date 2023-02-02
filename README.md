# Binary diff/patch utility

bsdiff and bspatch are tools for building and applying patches to binary files. By using suffix sorting (specifically, Larsson and Sadakane's qsufsort) and taking advantage of how executable files change, bsdiff routinely produces binary patches 50-80% smaller than those produced by Xdelta, and 15% smaller than those produced by .RTPatch (a $2750/seat commercial patch tool).

## bsdiff-4.3
http://www.daemonology.net/bsdiff/

## bzip2-1.0.6
https://sourceforge.net/projects/bzip2/

## Build

```shell
mkdir -p build && cd build
cmake .. && make install
```
