# SHACL-S

Scala implementation of SHACL.

This project contains an implementation of
[SHACL](http://w3c.github.io/data-shapes/shacl/) in Scala.

[![Build Status](https://travis-ci.org/weso/shacl-s.svg?branch=master)](https://travis-ci.org/weso/shacl-s)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/da1290bfb5ea4f4e9dbf4074960d06c3)](https://www.codacy.com/gh/weso/shacl-s?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=weso/shacl-s&amp;utm_campaign=Badge_Grade)
[![codecov](https://codecov.io/gh/weso/shacl-s/branch/master/graph/badge.svg)](https://codecov.io/gh/weso/shacl-s)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/es.weso/shacl_2.13/badge.svg)](https://maven-badges.herokuapp.com/maven-central/es.weso/shacl_2.13)

## Introduction

This project contains an implementation of [SHACL](https://www.w3.org/TR/shacl/) in Scala.

## Installation and compilation

The project uses [sbt](http://www.scala-sbt.org/) for compilation as well as Java 1.8.

* `sbt test` compiles and runs the tests

## Usage

Once compiled, the program can be run as a command line tool.
It is possible to run the program inside `sbt` as:

### Validating RDF data with SHACL

Example:

```sh
sbt "run --data examples/shacl/good1.ttl 
         --engine ShaClex"
```

### Interactive mode with `sbt`

It is usually faster to run the `sbt` command, which opens the interactive `sbt` shell and inside that shell, execute the different commands.

```sh
$ sbt
... several information about loading libraries
sbt> run -d examples/shacl/good1.ttl --engine ShaClex  
```

### Binary mode

The fastest way to run Shacl-s is to compile the code and generate a binary.
The following command:

```sh
$ sbt universal:packageBin
...generates the file...
target/universal/shacl-s-N.N.N.zip
```

which contains the compressed binary code.

## Implementation details

* The engine is based on Monads using the [cats library](http://typelevel.org/cats/)
* JSON encoding and decoding uses the Json structure [defined here](https://shexspec.github.io/spec/) and is implemented using [Circe](https://github.com/travisbrown/circe)

## Compatibility tests

The current implementation passes all [shacl-core tests](https://w3c.github.io/data-shapes/data-shapes-test-suite/). In order to generate the EARL report, run: 
 
```
$ sbt 
[...]
sbt:shaclex> project shacl 
sbt:shacl> testOnly es.weso.shacl.report.ReportGeneratorCompatTest
```

## Publishing to OSS-Sonatype

This project uses [the sbt ci release](https://github.com/olafurpg/sbt-ci-release) plugin for publishing to [OSS Sonatype](https://oss.sonatype.org/).

##### SNAPSHOT Releases
Open a PR and merge it to watch the CI release a -SNAPSHOT version

##### Full Library Releases
1. Push a tag and watch the CI do a regular release
2. `git tag -a v0.1.0 -m "v0.1.0"`
3. `git push origin v0.1.0`
_Note that the tag version MUST start with v._ 
 
## More information

* More information about SHACL can be read in the [Validating RDF data](http://book.validatingrdf.com) co-authored by one of the authors.
* This project was originally part of [SHaclEx](http://shaclex.weso.es) but we decided to modularize that project and keep the SHACl implementation in its own repository.
* An online demo based on this library is available at [http://rdfshape.weso.es](http://rdfshape.weso.es).
* Another online demo based on this library customized for Wikidata is available at [http://wikishape.weso.es](http://wikishape.weso.es).
* This project was based on [ShExcala](http://labra.github.io/ShExcala/) which was focused on Shape Expressions only.

## Author & contributors

* Author: [Jose Emilio Labra Gayo](http://labra.weso.es)

Contributors:

* [Eric Prud'hommeaux](https://www.w3.org/People/Eric/)
* [Bogdan Roman](https://github.com/bogdanromanx)
* [Toni Cebrían](http://www.tonicebrian.com/)
* [Andrew Berezovskyi](https://github.com/berezovskyi)

## Adopters

* [RDFShape](http://rdfshape.weso.es): An online demo powered by this library.
* [Wikishape](http://wikishape.weso.es): An online demo powered by this library for Wikidata.
* [Eclipse lyo](http://www.eclipse.org/lyo/): An SDK and a modelling environment to design and develop linked data applications based on the [OSLC standards](http://open-services.net/). The validation library is [lyo-validation](https://github.com/eclipse/lyo-validation).

## Contribution

Contributions are greatly appreciated.
Please fork this repository and open a
pull request to add more features or [submit issues](https://github.com/labra/shaclex/issues)
