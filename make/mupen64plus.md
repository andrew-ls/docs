# Mupen64Plus

## Compiling Plugins

These are the plugins we will be compiling:

1. [Core](https://github.com/mupen64plus/mupen64plus-core)
2. [cxd4's RSP](https://github.com/mupen64plus/mupen64plus-rsp-cxd4)
3. [Angrylion RDP Plus](https://github.com/ata4/angrylion-rdp-plus)
4. [SDL Audio](https://github.com/mupen64plus/mupen64plus-audio-sdl)
5. [SDL Input](https://github.com/mupen64plus/mupen64plus-input-sdl)

### Dependencies

To compile the plugins, certain libraries and development headers are required.
These are the packages available for Fedora to fulfil the dependencies of all
of the plugins:

* `mesa-libGLU-devel`: OpenGL utility library headers
* `nasm`: Netwide Assembler
* `SDL2-devel`: SDL 2 headers

The following two are optional for the SDL Audio Plugin:

* `libsamplerate-devel`: Secret Rabbit Code headers
* `speexdsp-devel`: Speex headers

### Compiling

#### Basics

For each plugin, clone the respective repository and navigate to `projects/unix`
in the working tree. A `Makefile` will be present. All you need to do now is
execute the `make` command against the `all` target:

````````````````````````````````````````````````````````````````````````````` sh
make all
````````````````````````````````````````````````````````````````````````````````

A shared object file ending with "`.so`" will have been created in the current
directory, which you can place in the appropriate plugins directory for
Mupen64Plus.

The above works fine for the Core plugin, however for other plugins we might
need an environment variable to point towards the core headers for Mupen64Plus:

````````````````````````````````````````````````````````````````````````````` sh
APIDIR='<APIDIR>' make all
````````````````````````````````````````````````````````````````````````````````

Where `<APIDIR>` is the absolute path to the `src/api` directory within the
`mupen64plus-core` plugin's repository.

#### Optimization

For improved performance it is possible to define some additional flags during
compilation. These are controlled with the `OPTFLAGS` environment variable. The
default `OPTFLAGS` are `-O3 -flto`, so we should include them as the base for
any changes we make.

The `-mtune` switch will compile including optimizations for a given platform,
without breaking compatibility for older iterations of the architecture. A value
of `native` will target the platform of the current machine, which we will use:

````````````````````````````````````````````````````````````````````````````` sh
OPTFLAGS='-O3 -flto -mtune=native' APIDIR='<APIDIR>' make all
````````````````````````````````````````````````````````````````````````````````

#### Angrylion RDP Plus

The procedure for compiling the `video-angrylion-plus` plugin differs slightly;
run the following commands in the root of the repository before running `make`
as above:

````````````````````````````````````````````````````````````````````````````` sh
mkdir build
cd build
cmake ..
````````````````````````````````````````````````````````````````````````````````
