# Serial Communication Library

This is a fork of an exccelent cross-platform library for interfacing with rs-232 serial like ports written in C++ [serial](https://github.com/wjwwood/serial) by [wjwwood](https://github.com/wjwwood). 

### Documentation

Website: http://wjwwood.github.com/serial/

API Documentation: http://wjwwood.github.com/serial/doc/1.1.0/index.html

### Dependencies

Required:
* [cmake](http://www.cmake.org) - buildsystem

Optional (for documentation):
* [Doxygen](http://www.doxygen.org/) - Documentation generation tool
* [graphviz](http://www.graphviz.org/) - Graph visualization software

### Install

Get the code:

    git clone https://github.com/wjwwood/serial.git

Build:

    mkdir build && cd build && cmake .. && make

Install:

    sudo make install

### Usage
In your cmake project:
```
find_package(serial 1.0 REQUIRED)
target_link_libraries(${PROJECT_NAME} serial::serial)
```

### License

The MIT License

Copyright (c) 2012 William Woodall, John Harrison

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

### Orignal Authors
Thanks to
    * William Woodall <wjwwood@gmail.com>
    * John Harrison <ash.gti@gmail.com>
