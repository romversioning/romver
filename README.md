# RomVer – Romantic Versioning

## Spec Summary

Version numbers are defined as `PROJECT.MAJOR.MINOR`, where you increment the:

1. `PROJECT` segment when you want the version to be considered a new, separate project (e.g. Sdl 2.28 to Sdl 3.0).
2. `MAJOR` segment when you make breaking changes.
3. `MINOR` segment when you make non-breaking changes (e.g. adding functionality or bug fixes in a backward-compatible manner).

Additional labels for pre-release and build metadata are available as extensions to the PROJECT . MAJOR . MINOR format.

## Introduction

This is an alternative to the [SemVer](https://semver.org/) format, focusing instead on defining and standardizing version numbers based off the ways in which people naturally treat them. Many large and popular projects (e.g. Node, Rails, PHP, jQuery, NPM, the Linux Kernel, and many more) deny using SemVer for various reasons, all of which can be traced back to human intuition. This standard attempts to work with intuition instead of overriding it.

The Romantic Versioning specification was originally authored by [Daniel V](https://web.archive.org/web/20221003075344/http://blog.legacyteam.info/2015/12/romver-romantic-versioning/) in 2015, and this open and public repository has the task of maintaining, extending, polishing, and popularizing this standard. If you'd like to leave feedback, please [open an issue on GitHub](https://github.com/romversioning/romver/issues).

## Links
* [License](https://creativecommons.org/licenses/by/4.0/)
* [FAQ](FAQ.md)
* [Contributing](CONTRIBUTING.md)
* [Code of Conduct](CODE_OF_CONDUCT.md)

## Romantic Versioning Specification (RomVer)

1. Software using Romantic Versioning must declare a public API. This API could be declared in the code itself or exist strictly in documentation. However it is done, it should be precise and comprehensive.
2. A normal version number must take the form X.Y.Z where X, Y, and Z are non-negative integers and must not contain leading zeroes. X is the project version, Y is the major version, and Z is the minor version. Each element must increase numerically. For instance: 1.9.0 -> 1.10.0 -> 1.11.0.
3. Once a versioned package has been released, the contents of that version must not be modified. Any modifications must be released as a new version.
4. Project version zero (0.y.z) is for initial development. Anything may change at any time. The public API should be considered something other than stable.
5. Version 1.0.0 defines the public API. The way the version number is incremented after this release depends on this public API and how it changes.
6. Minor version Z (x.y.Z | Z > 0) must be incremented if backward-compatible bug fixes (internal change that fixes incorrect behavior) are introduced or if new backward-compatible functionality is introduced to the public API.
7. Major version Y (x.Y.z | Y > 0) must be incremented if any backward-incompatible changes are introduced to the public API. It must be incremented if any public API functionality is marked as deprecated. It may be incremented if substantial new functionality or improvements are introduced within the private code. It may include minor level changes. The minor version must be reset to 0 when the major version is incremented.
8. Project version X (X.y.z | X > 0) may be incremented if any conceptual or backward incompatible change is introduced to the public API. It may include major and minor level changes. Major and minor versions must be reset to 0 when the project version is incremented.
9. A pre-release version may be denoted by appending a hyphen, and a series of dot-separated identifiers immediately following the minor version. Identifiers must comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers must not be empty. Numeric identifiers must not include leading zeroes. Pre-release versions have a lower precedence than the associated normal version. A pre-release version indicates that the version is unstable and might not satisfy the intended compatibility requirements as denoted by its associated normal version.<br>
Examples: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
10. Build metadata may be denoted by appending a plus sign and a series of dot-separated identifiers immediately following the minor or pre-release version. Identifiers must comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers must not be empty. Build metadata should be ignored when determining version precedence. Thus two versions that differ only in the build metadata, have the same precedence.<br>
Examples: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
11. Precedence refers to how versions are compared when ordered. Precedence must be calculated by separating the version into the project, major, minor, and pre-release identifiers in that order (Build metadata does not figure into precedence). Precedence is determined by the first difference when comparing each of these identifiers from left to right as follows: Project, major, and minor versions are always compared numerically.<br>
Example: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1.<br>
When project, major, and minor are equal, a pre-release version has lower precedence than a normal version.<br>
Example: 1.0.0-alpha < 1.0.0.<br>
Precedence for two pre-release versions with the same project, major, and minor version must be determined by comparing each dot separated identifier from left to right until a difference is found as follows: identifiers consisting of only digits are compared numerically and identifiers with letters or hyphens are compared lexically in ASCII sort order. Numeric identifiers always have lower precedence than non-numeric identifiers. A larger set of pre-release fields has a higher precedence than a smaller set if all of the preceding identifiers are equal.<br>
Example: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

## License

Creative Commons - CC BY 4.0
[http://creativecommons.org/licenses/by/3.0/](https://creativecommons.org/licenses/by/4.0/)
