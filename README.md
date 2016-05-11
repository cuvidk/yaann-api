#Y.A.A.N.N.C.

	Yet Another Artificial Neural Network Classifier.

This provides a pretty simple API that anyone can use for classification. All you need to do is to 
collect some training set, train the neural network on it and then you can provide the network an item that 
you want to classify and it will do it for you. This can be achieved pretty easy, just have a look at the examples.

To make the training process faster, a vectorized implementation of the backpropagation algorithm was
needed. I didn't write the matrix API, since there are plenty linear algebra libraries that provide very fast 
matrix operations, so [armadillo](arma.sourceforge.net) was used instead.

##Installation

First you'll have to clone this repository on your machine. I'll use the shorthand {yaannc-root} to refer to the
root directory of the cloned repo.
You'll also have to satisfy the armadillo library dependency. To do that please visit [armadillo's](arma.sourceforge.net) website and install the library that corresponds to your platform. For any platform, you'll find the 
installation details in the README.txt file that can be found in the armadillo archive that you've downloaded. 
For unix platforms the installation is detailed very well so the installation should go on pretty smooth. On the
other hand, windows installation for armadillo is pretty confusing so I added under `{yaannc-root}/install/windows/armadillo` everything you need so you can use yaannc library.

###Linux

* Open up a terminal;
* Make sure you have g++ installed. If you have a Debian based system you can run the following command
to install g++:

```bash
$ sudo apt-get install g++
```

* cd to `{yaannc-root}/install/linux` where a Makefile is located;
* Run the following command so the libyaannc.a file can be generated:
	
```bash
$ make
```

* Run the following command to install the yannc library and includes to your system:

```bash
sudo make install
```

* You're done. You can now try out one of the examples presented in the examples section. To compile your source
code you can use the following command:

```bash
$ g++ {your_source_files} -lyaannc -larmadillo
```
If you want to uninstall the library from the system, in `{yaannc-root}/install/linux` run the following command:

```bash
sudo make uninstall
```

###Windows

I'll only cover how to configure a Visual Studio project so you can use YAANNC library.

* Create a new empty Visual Studio C++ project;
* Right click on the newly created project and select `Properties`. Under `Configuration Properties->C/C++->General->Additional Include Directories` add the following:
  * the include directory of the armadillo library. If you didn't install armadillo, you can use the include
directory `{yaannc-root}/install/windows/armadillo/include`;
  * the include directory of the yaannc library which is located under `{yaannc-root}/install/windows/yaannc/include`.
* Right click on project, select `Properties`. Under `Configuration Properties->Linker->Additional Library Directories` add the following:
  * armadillo's library directory. The same as above, if you didn't install armadillo, you can use the directory
`{yaannc-root}/install/windows/armadillo/lib`, but take note that this directory includes the library files for 
x64 configurations only, so in the next step you will also have to use the x64 yaannc library files. If you 
want x86 lib files, you will have to get them yourself.
  * the yaannc library directory, located under `{yaannc_root}/install/windows/yaannc/lib`. You can further see
that there are available lib folders for x86 and for x64, so choose only the one that you need.
* Right click on project, select `Properties`. Under `Configuration Properties->Linker->Input->Additional Dependencies` add all the .lib files present in the directory selected at the previous step.
* Now you should be able to compile your project, so check the examples section and make a test. In order to run
it you will need to add the .dll files that come with armadillo library (e.g. blas-win64-MT.dll lapack-win64-MT.dll) in the Debug / Realease folder generated by Visual Studio after building your project, or alternatively add
the folder that contains them to PATH environment variable. You're done.
