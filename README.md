# cats-scalacheck [![Build Status][travis-badge]][travis-url] [![Sonatype Release][sonatype-badge]][sonatype-url]

This is a fork, you should probably not contribute here, and just go to the main project. If I release under this organization, I'll use version numbers of the form `w.x.y.z`, which will contain all features of `w.x.y` from the main project. Any additional features will also be submitted as PRs to the main project.

Inspiration Was Taken From the never published cats-check. Instances for Cats for scalacheck types. So all credit to [erik-stripe](https://github.com/erik-stripe) and the last maintainer [mdedetrich](https://github.com/mdedetrich) for their original work on this that helped me build this.

## Quick Start

`cats-scalacheck` is published for scala 2.12 and 2.13, and scalajs 1.0.0. If you require scalajs 0.6 and/or scala 2.11, you may use the last version of this project: `0.2.0`.

To use cats-scalacheck in an existing SBT project, add the following dependency to your `build.sbt`:

```scala
libraryDependencies += "io.chrisdavenport" %% "cats-scalacheck" % "<version>"
```

For use with scalajs:

```scala
libraryDependencies += "com.clovellytech" %%% "cats-scalacheck" % "<version>"
```


## Getting Started

```scala
import org.scalacheck._
import org.scalacheck.cats.implicits._
import cats.Applicative
import cats.implicits._

val apComposition: Gen[(Int, String)] = Applicative[Gen].product(
  Arbitrary.arbitrary[Int],
  Arbitrary.arbitrary[String]
)
```

## Instances

### Gen

- `Alternative[Gen]`
- `Monad[Gen]`
- `FunctorFilter[Gen]`
- `Monoid[A] => Monoid[Gen[A]]`
- `Semigroup[A] => Semigroup[Gen[A]]`

### Cogen

- `ContravariantSemigroupal[Cogen]`
- `MonoidK[Cogen]`

## Why in org.scalacheck

This was necessary because scalacheck makes some of their instances package private that
are required to roll these meaningfully.


[travis-badge]: https://travis-ci.com/clovellytech/cats-scalacheck.svg?branch=master "Build Status"
[travis-url]: https://travis-ci.com/clovellytech/cats-scalacheck "Build Status"
[sonatype-badge]: https://img.shields.io/nexus/r/com.clovellytech/cats-scalacheck_2.12.svg?server=https://oss.sonatype.org "Sonatype Releases"
[sonatype-url]: https://oss.sonatype.org/content/groups/public/com/clovellytech/ "Sonatype Releases"
