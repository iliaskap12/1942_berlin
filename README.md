# 1942 - London to Berlin

__"1942 - London to Berlin"__ is a recreation of the classic arcade game 1942, developed as a C++ and OOP practice project for school with the *[Simple Game Graphics](https://github.com/cgaueb/sgg)* library.

## How it differs from the original:
  - *Instead of flying from the USA to Tokyo, we are piloting a Supermarine Spitfire from London straight to Berlin*
  - *It has real German aircrafts with their original sounds* 
  - *Enemy Stuka aircrafts will be all over, and their sound will make them more than noticable*

## How to contribute:

  Before you clone the project, first you need to install the SGG library. The original SGG library does not yet come with out of the box CMake support, but soon it will (it has a pending pull request for it). Until then, you can clone *[my fork of the library](https://github.com/iliaskap12/sgg)* where I merged the pull request prematurely, but it seems to work fine. To build the library on your system you will need the vcpkg package manager, which can be installed on all platforms following the instructions on the *[official microsoft documentation page](https://docs.microsoft.com/en-us/cpp/build/install-vcpkg?view=msvc-160&tabs=linux)*.
  
  First, you need to clone the forked library. On linux, type the following commands:
  ```sh
  $ cd
  $ git clone https://github.com/iliaskap12/sgg.git
  ```
  These commands will install the source library in your home directory. Then, following the original instructions of the author on how to build the library using CMake (see below but for more information read the [README.md](https://github.com/iliaskap12/sgg/blob/main/README.md) of the original author, currently available at my fork github page)
  ```sh
$ cd ~/sgg
$ cmake -B build -DCMAKE_BUILD_TYPE=Release \
                -DCMAKE_EXPORT_PACKAGE_REGISTRY=ON \
                -DCMAKE_TOOLCHAIN_FILE=$VCPKG_INSTALL_DIR/scripts/buildsystems/vcpkg.cmake \
                -DVCPKG_TARGET_TRIPLET=x64-windows-static
```
you __*will*__ need to change the ```$VCPKG_INSTALL_DIR``` with an __*absolute path*__ of the directory where the vcpkg package manager has been installed (initially I thought that ```$VCPKG_INSTALL_DIR``` was a CMake macro command that would find the install directory of the vcpkg package manager automagically because, as I understand, using the vcpkg package manager with CMake is a very common toolchain). Then, you will need to change the registries to match your system (e.g. if you are on linux, you will need to change `x64-windows-static` to `x64-linux`). Finally, you might need to download any missing dependencies of the library for your operating system. For example, on my machine the glm dependency was missing, so I had to download it using the following commands:
```sh
$ cd
$ sudo apt update
$ sudo apt install libglm-dev
```
Next, you need to build the library using the following command:
```sh
$ cd sgg
$ cmake --build build
```
The above command will build the library on your system. 
We are almost done here. In the CMakeLists.txt of the root directory of the project you need the two following commands (if you clone the project they are already included, but for completeness sake I reference them here as well):
```
find_package(sgg REQUIRED)
target_link_libraries(${PROJECT_NAME} PRIVATE sgg::sgg)
```
To clone the project, cd to your desired destination and run:
```sh
$ git clone https://github.com/iliaskap12/1942_berlin.git
```

After you've completed all these steps you are ready to contribute any way you want, any cool feature/idea of yours or any requirement listed in the requirements document (pending). Don't push directly to the master branch, instead create a branch and push from there, and we will handle the integration at the pull request.
 