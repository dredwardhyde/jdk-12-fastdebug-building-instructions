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
