# pixi symbolic link bug

Repro:

```
$ docker run --rm -v $PWD:$PWD -w $PWD  -it ghcr.io/prefix-dev/pixi:latest pixi list
  x failed to instantiate a prefix for 'default'
  |-> failed to link ncurses-6.5-h0425590_0.conda
  |-> failed to link 'share/terminfo/n/ncr260vt300wpp'
  |-> failed to copy file to destination
  `-> Symbolic link loop (os error 40)
```

```
root@b6800a4f9fc8:/tmp/pixi-repro# pixi info
      Pixi version: 0.23.0
          Platform: linux-aarch64
  Virtual packages: __unix=0=0
                  : __linux=6.4.16=0
                  : __glibc=2.35=0
                  : __archspec=1=m1
         Cache dir: /root/.cache/rattler/cache
      Auth storage: /root/.rattler/credentials.json

Project
------------
              Name: pixi-repro
           Version: 0.1.0
     Manifest file: /tmp/pixi-repro/pixi.toml
  Config locations:
      Last updated: 03-06-2024 14:48:28

Environments
------------
       Environment: default
          Features: default
          Channels: conda-forge
  Dependency count: 1
      Dependencies: pytest
 PyPI Dependencies: python-git
  Target platforms: linux-64, osx-arm64, linux-aarch64
```
