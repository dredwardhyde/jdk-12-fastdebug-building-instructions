### How to make fastdebug JDK 12 build on macOS 14 Mojave

- macOS version
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/8.png" width="580"/>

- Install Xcode 10
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/10.png" width="700"/>

- Install Xcode Command Line Tools

```sh
xcode-select --install
```
Output of the following commands should look like that
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/7.png" width="1000"/>

- Install https://brew.sh/
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/14.png" width="700"/>

- Install autoconf

```sh
brew install autoconf
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/12.png" width="700"/>

- Install automake

```sh
brew install automake
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/13.png" width="700"/>

- Install mercurial

```sh
brew install mercurial
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/11.png" width="700"/>

- Install Oracle JDK 11
https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/9.png" width="700"/>

- Clone jdk12u from repository

```sh
hg clone http://hg.openjdk.java.net/jdk-updates/jdk12u/
```

- Download jtreg and add to PATH in ~/.bash_profile https://openjdk.java.net/jtreg/

- Create build configuration with following commands
```sh
cd jdk12u
./configure --enable-debug --disable-warnings-as-errors --with-jtreg
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/4.png" width="1100"/>

- Build JDK
```sh
make CONF=debug
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/5.png" width="1000"/>

- Check if build is alive
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/6.png" width="800"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/1.png" width="650"/>

- Optionally run tier 1 tests
```sh
make run-test-tier1
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/2.png" width="750"/>


### How to make fastdebug JDK 12 build on Windows 10

#### Install Visual Studio 2017
- I've choosed following components for installation:
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_01-12-35.png" width="1000"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_01-12-54.png" width="1000"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_11-45-36.png" width="700"/>

#### Install JDK 11 as bootstrap jdk (coule be from Oracle or any OpenJDK distribution):
- I've used this version: https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html
- Add JAVA_HOME:
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_01-27-37.png" width="700"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_01-28-41.png" width="700"/>

#### Download jtreg from https://openjdk.java.net/jtreg/ and add jtreg and bootstrap JDK to PATH:
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-48-52.png" width="700"/>

#### Install Mercuarial for Windows from https://www.mercurial-scm.org/downloads
#### Download cygwin from https://cygwin.com/ and install it with following command:
```sh
setup-x86_64 -q -P autoconf -P make -P unzip -P zip -P binutils -P m4 -P cpio -P gawk -P file -P procps-ng -P automake
```
#### Create short names for Visual Studio and Windows Kits folders using following commands (short names are given as examples):
```sh
cd "C:\Program Files (x86)"
fsutil file setshortname "Windows Kits" "WinKits"
fsutil file setshortname "Microsoft Visual Studio" "micro17"
```
#### Check that short names are correctly created using command:
```sh
dir /x "."
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_01-32-33.png" width="700"/>

#### Clone JDK 12u using command:
```sh
hg clone http://hg.openjdk.java.net/jdk-updates/jdk12u/
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_01-37-09.png" width="700"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-04-00.png" width="700"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-20-28.png" width="700"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-22-04.png" width="700"/>

#### Create JDK 12 build configuration in cygwin using following command from the root folder of cloned repo:
```sh
cd /cygdrive/c/<path to repo>
./configure --enable-debug --disable-warnings-as-errors --with-target-bits=64 --with-jtreg
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-26-24.png" width="1000"/>

#### Check created pathes for correctness (no whitespaces, etc):
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-26-04.png" width="1000"/>

#### Result should look like this:
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-25-35.png" width="1000"/>

#### Now we are ready to make JDK build using command:
```sh
make CONF=debug
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-31-29.png" width="1000"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-40-59.png" width="1000"/>

```sh
make images
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-42-20.png" width="1000"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-45-02.png" width="1000"/>

#### Test if our build is alive:

```sh
cd build/windows-x86_64-server-fastdebug/images/jdk/bin/
./java -Xinternalversion
./java -version
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-47-02.png" width="1000"/>

#### Run tier1 tests from root folder:

```sh
make run-test-tier1
```
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_02-58-13.png" width="1000"/>
<img src="https://raw.githubusercontent.com/komesergey/jdk-12-fastdebug-building-instructions/master/image_2019-04-20_11-26-20.png" width="1000"/>
