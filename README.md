# pixi symbolic link bug

Repro:

```
$ docker run --rm -v $PWD:$PWD -w $PWD  -it pixi:latest pixi list
  x failed to instantiate a prefix for 'default'
  |-> failed to link ncurses-6.5-h0425590_0.conda
  |-> failed to link 'share/terminfo/n/ncr260vt300wpp'
  |-> failed to copy file to destination
  `-> Symbolic link loop (os error 40)
```
