[![Gitter](https://badges.gitter.im/couchbase/couchbase-lite-java-core.svg)](https://gitter.im/couchbase/couchbase-lite-java-core?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

This is a "portable java" version of the Couchbase Lite.  

To see how this fits into the overall architecture, see the [Couchbase Lite Project Structure](https://github.com/couchbase/couchbase-lite-android/wiki/Project-structure).

# Get the code
```
$ git clone https://github.com/couchbase/couchbase-lite-java.git
$ cd couchbase-lite-java
$ git submodule update --init --recursive
```

# Build and test

### Requirements

* JDK 1.7+

* Toolchains for compiling native libraries as follows :

	| Operating System | Tool Chain       | Notes
	| ---------------- |:----------------:|-------------
	| Linux            | GCC and G++      |
	| Mac OSX          | GCC or Clang     |
	| Windows          | Visual C++       | Install Visual Studio 2015.

* To setup a Linux cross complier to compile both x86 and x86_64 linux native libraries on 64 bit machine, you may setup your toolchain as below :

	```
	$ sudo apt-get install gcc-multilib
	$ sudo apt-get install g++-multilib
	``` 
* Oracle Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files. This is required for Database Encryption feature to use 256 AES Bit Key. Please follow the links below to download and install the policy files:

       - Java 1.7 http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html
       - Java 1.8 http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html

### Build and Test Steps - Command Line

Note: Currently we are sharing the test suits with [Couchbase-lite-android](https://github.com/couchbase/couchbase-lite-android.git) project and the following steps will copy the test classes over and run the test suit.

1. Clone Couchbase-lite-android project<br>`$ git clone https://github.com/couchbase/couchbase-lite-android.git` at the same folder where the couchbase-lite-java is located (parent folder of couchbase-lite-java).
1. Go to your couchbase-lite-java, build the project and run the tests<br>`$ ./gradlew clean && ./gradlew test`

If you need to see the test output to debug them, you can run `./gradlew --debug --info test`

*Note: there seems to be no way to see the test output when using the command line, so if you need to see the test output, use the IntelliJ IDE instead*

### Build and Test Steps - IntelliJ

1. Build on command line - run `$ ./gradlew build`
1. Clone Couchbase-lite-android project<br>`$ git clone https://github.com/couchbase/couchbase-lite-android.git` at the same folder where the couchbase-lite-java is located (parent folder of couchbase-lite-java).
1. Open IntelliJ and import project by selecting settings.gradle
1. In IntelliJ project window, browse to /src/test/java/
1. Right-click on an individual test or package and choose Run Test ..

# Build and Package the library

```
$ ./gradlew distZip
```
Note: The packaged file will be located at build/distributions.
