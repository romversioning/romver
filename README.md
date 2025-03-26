# Romantic Versioning (RomVer)

## Spec Summary

Version numbers are defined as `"HUMAN.MAJOR.MINOR"`, where you increment the:

1. `HUMAN` segment when you make any conceptual change, major rewrite, major documentation change, or any other change which requires additional HUMAN involvement.
2. `MAJOR` segment when you make breaking changes.
3. `MINOR` segment when you make non-breaking changes (e.g. adding functionality or bug fixes in a backward-compatible manner).

Additional labels for pre-release and build metadata are available as extensions to the HUMAN . MAJOR . MINOR format.

## Introduction

This is an alternative to the [SemVer](https://semver.org/) format, focusing instead on defining and standardizing version numbers based off the ways in which people naturally treat them. Many large and popular projects (e.g. Node, Rails, PHP, jQuery, NPM, the Linux Kernel, and many more) deny using SemVer and instead opt to just base their versions off intuition. RomVer acknowledges the importance of intuition regarding version numbers and attempts to standardize versions in a way that is both extremely intuitive and extremely useful.

The Romantic Versioning specification was originally authored by [Daniel V](https://web.archive.org/web/20221003075344/http://blog.legacyteam.info/2015/12/romver-romantic-versioning/) in 2015, and this open and public repository has the task of maintaining, extending, polishing, and popularizing this standard. If you'd like to leave feedback, please [open an issue on GitHub](https://github.com/romversioning/romver/issues).

## Why was this made?

This was made to fix the confusion that SemVer often creates regarding MAJOR changes. When a project releases a v2.0, people don't automatically think of it as a simple breaking change as they should, they think of it as being an extremely big deal. And conversely, when a project releases a v54.0, people don't automatically think of it as a simple breaking change as they should, they think of it as another small and tedious step that isn't noteworthy.

For whatever reason, humans seem to naturally put a lot of personal attachment in the first number of a version, and this standard attempts to work with that fact instead of overriding it. 

## Why should this be used?

- Users (including developers) are less confused and are quicker to pick up on the importance of version changes (as described above).
- It conveys more information to users
- - The MINOR and PATCH segments in SemVer are both backwards-compatible, so they're identical when it comes to whether or not users should update. Here, they're combined into a single segment.
- - The PROJECT and MAJOR segments denote differing levels of breaking changes, with MAJOR increments likely being easy to update to and PROJECT increments likely being not easy to update to.
- It is compatible with systems that expect SemVer. This mainly uses three numerical segments, which makes it compatible with essentially every system that takes a version number, plus there are rules for how to compact a more complex version to just three integers.
- (Extra) The specification is barely even needed since it basically just states what people already expect when looking at the three numbers.
- (Extra) You don't have to do something crazy like "Project v2 v0.1.0" if you want to radically transform your project.

## Links
* [License](https://creativecommons.org/licenses/by/4.0/)
* [FAQ](FAQ.md)
* [Contributing](CONTRIBUTING.md)
* [Code of Conduct](CODE_OF_CONDUCT.md)

## Romantic Versioning Specification (RomVer)

1. Software using Romantic Versioning must declare a public API. This API could be declared in the code itself or exist strictly in documentation. However it is done, it should be precise and comprehensive.
2. A normal version number must take the form X.Y.Z where X, Y, and Z are non-negative integers and must not contain leading zeroes. X is the human version, Y is the major version, and Z is the minor version. Each element must increase numerically. For instance: 1.9.0 -> 1.10.0 -> 1.11.0.
3. Once a versioned package has been released, the contents of that version must not be modified. Any modifications must be released as a new version.
4. Human version zero (0.y.z) is for initial development. Anything may change at any time. The public API should be considered something other than stable.
5. Version 1.0.0 defines the public API. The way the version number is incremented after this release depends on this public API and how it changes.
6. Minor version Z (x.y.Z | Z > 0) must be incremented if backward-compatible bug fixes (internal change that fixes incorrect behavior) are introduced or if new backward-compatible functionality is introduced to the public API.
7. Major version Y (x.Y.z | Y > 0) must be incremented if any backward-incompatible changes are introduced to the public API. It must be incremented if any public API functionality is marked as deprecated. It may be incremented if substantial new functionality or improvements are introduced within the private code. It may include minor level changes. The minor version must be reset to 0 when the major version is incremented.
8. Human version X (X.y.z | X > 0) may be incremented if any conceptual or backward incompatible change is introduced to the public API. It may include major and minor level changes. Major and minor versions must be reset to 0 when the human version is incremented.
9. A pre-release version may be denoted by appending a hyphen, and a series of dot-separated identifiers immediately following the minor version. Identifiers must comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers must not be empty. Numeric identifiers must not include leading zeroes. Pre-release versions have a lower precedence than the associated normal version. A pre-release version indicates that the version is unstable and might not satisfy the intended compatibility requirements as denoted by its associated normal version.<br>
Examples: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
10. Build metadata may be denoted by appending a plus sign and a series of dot-separated identifiers immediately following the minor or pre-release version. Identifiers must comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers must not be empty. Build metadata should be ignored when determining version precedence. Thus two versions that differ only in the build metadata, have the same precedence.<br>
Examples: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
11. Precedence refers to how versions are compared when ordered. Precedence must be calculated by separating the version into the human, major, minor, and pre-release identifiers in that order (Build metadata does not figure into precedence). Precedence is determined by the first difference when comparing each of these identifiers from left to right as follows: Human, major, and minor versions are always compared numerically.<br>
Example: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1.<br>
When human, major, and minor are equal, a pre-release version has lower precedence than a normal version.<br>
Example: 1.0.0-alpha < 1.0.0.<br>
Precedence for two pre-release versions with the same human, major, and minor version must be determined by comparing each dot separated identifier from left to right until a difference is found as follows: identifiers consisting of only digits are compared numerically and identifiers with letters or hyphens are compared lexically in ASCII sort order. Numeric identifiers always have lower precedence than non-numeric identifiers. A larger set of pre-release fields has a higher precedence than a smaller set if all of the preceding identifiers are equal.<br>
Example: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

## License

[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)
