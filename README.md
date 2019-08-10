[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![star this repo](http://githubbadges.com/star.svg?user=proximax-storage&repo=java-xpx-ipfs-sdk&style=flat)](https://github.com/proximax-storage/java-xpx-ipfs-sdk)
[![fork this repo](http://githubbadges.com/fork.svg?user=proximax-storage&repo=java-xpx-ipfs-sdk&style=flat)](https://github.com/proximax-storage/java-xpx-ipfs-sdk/fork)
[![Coverage Status](https://coveralls.io/repos/github/proximax-storage/java-xpx-ipfs-sdk/badge.svg?branch=master)](https://coveralls.io/github/proximax-storage/java-xpx-ipfs-sdk?branch=master)
[![Build Status](https://travis-ci.com/proximax-storage/java-xpx-ipfs-sdk.svg?branch=master)](https://travis-ci.com/proximax-storage/java-xpx-ipfs-sdk)

# ProximaX IPFS Java API #

> A Java implementation of the IPFS http api

## ProximaX Forked Version
This is a forked version of IPFS [java-ipfs-api](https://github.com/ipfs/java-ipfs-api) project

## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [Building](#building)
- [Contribute](#contribute)
- [License](#license)

## Install

### Official releases

You can use this project by including `ipfs.jar` from one of the [releases](https://github.com/ipfs/java-ipfs-api/releases).

### Maven, Gradle, SBT

Package managers are supported through [JitPack](https://jitpack.io/#ipfs/java-ipfs-api/) which supports Maven, Gradle, SBT, etc.

for Maven, add the following sections to your pom.xml (replacing $LATEST_VERSION):
```
  <repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
  </repositories>

  <dependencies>
    <dependency>
      <groupId>com.github.ipfs</groupId>
      <artifactId>java-ipfs-api</artifactId>
      <version>$LATEST_VERSION</version>
    </dependency>
  </dependencies>
```

### Building

* Clone this repository
* Run `ant dist`
* Copy `dist/ipfs.jar` into your project. Appropriate versions of other [dependencies](#Dependencies) are also included in `dist/lib/`.
* Run tests using `ant test`.

## Usage

Create an IPFS instance with:
```Java
IPFS ipfs = new IPFS("/ip4/127.0.0.1/tcp/5001");
```

Then run commands like:
```Java
ipfs.refs.local();
```

To add a file use (the add method returns a list of merklenodes, in this case there is only one element):
```Java
NamedStreamable.FileWrapper file = new NamedStreamable.FileWrapper(new File("hello.txt"));
MerkleNode addResult = ipfs.add(file).get(0);
```

To add a byte[] use:
```Java
NamedStreamable.ByteArrayWrapper file = new NamedStreamable.ByteArrayWrapper("hello.txt", "G'day world! IPFS rocks!".getBytes());
MerkleNode addResult = ipfs.add(file).get(0);
```

To get a file use:
```Java
Multihash filePointer = Multihash.fromBase58("QmPZ9gcCEpqKTo6aq61g2nXGUhM4iCL3ewB6LDXZCtioEB");
byte[] fileContents = ipfs.cat(filePointer);
```

## Dependencies

Current versions of dependencies are included in the `./lib` directory.

* [multibase](https://github.com/multiformats/java-multibase)
* [multiaddr](https://github.com/multiformats/java-multiaddr)
* [multihash](https://github.com/multiformats/java-multihash)
* [cid](https://github.com/ipld/java-cid)

## Contribute

Feel free to join in. All welcome. Open an [issue](https://github.com/ipfs/java-ipfs-api/issues)!

This repository falls under the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).

[![](https://cdn.rawgit.com/jbenet/contribute-ipfs-gif/master/img/contribute.gif)](https://github.com/ipfs/community/blob/master/contributing.md)

## License

[MIT](LICENSE)
