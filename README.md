# RomVer – Romantic Versioning

## Summary

You are given a version number HUMAN . MAJOR . MINOR,  increment the:

1. HUMAN version when you make any conceptual change, major rewrite, major documentation change, or any other change which requires additional HUMAN involvement.
2. MAJOR  version when you make incompatible API changes,
3. MINOR version when you add functionality in a backward-compatible manner or fix with backward-compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the HUMAN . MAJOR . MINOR format.

## Introduction

This document is based on [SemVer spec](https://semver.org/) and details an alternative to SemVer.

This document is an attempt to extract 'versioning spec' from real-world usage of software versions (like in Node, Rails, PHP, jQuery, NPM, Linux Kernel), and it tries to enforce some rules to make software versioning predictable.

This document will probably have minor changes in the future. An alternative name for Romantic Versioning could also be Sentimental Versioning.

## Romantic Versioning Specification (RomVer)

1. Software using Romantic Versioning MUST declare a public API. This API could be declared in the code itself or exist strictly in documentation. However it is done, it should be precise and comprehensive.
2. A normal version number MUST take the form X.Y.Z where X, Y, and Z are non-negative integers and MUST NOT contain leading zeroes. X is the human version, Y is the major version, and Z is the minor version. Each element MUST increase numerically. For instance: 1.9.0 -> 1.10.0 -> 1.11.0.
3. Once a versioned package has been released, the contents of that version MUST NOT be modified. Any modifications MUST be released as a new version.
4. Human version zero (0.y.z) is for initial development. Anything may change at any time. The public API should be considered something other than stable.
5. Version 1.0.0 defines the public API. The way the version number is incremented after this release depends on this public API and how it changes.
6. Minor version Z (x.y.Z | Z > 0) MUST be incremented if backward-compatible bug fixes (internal change that fixes incorrect behavior) are introduced or of new backward-compatible functionality is introduced to the public API.
7. Major version Y (x.Y.z | Y > 0) MUST be incremented if any backward-incompatible changes are introduced to the public API. It MUST be incremented if any public API functionality is marked as deprecated. It MAY be incremented if substantial new functionality or improvements are introduced within the private code. It MAY include minor level changes. The minor version MUST be reset to 0 when the major version is incremented.
8. Human version X (X.y.z | X > 0) MAY be incremented if any conceptual or backward incompatible change is introduced to the public API. It MAY include major and minor level changes. Major and minor versions MUST be reset to 0 when the human version is incremented.
9. A pre-release version MAY be denoted by appending a hyphen, and a series of dot-separated identifiers immediately following the minor version. Identifiers MUST comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers MUST NOT be empty. Numeric identifiers MUST NOT include leading zeroes. Pre-release versions have a lower precedence than the associated normal version. A pre-release version indicates that the version is unstable and might not satisfy the intended compatibility requirements as denoted by its associated normal version.<br>
Examples: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
10. Build metadata MAY be denoted by appending a plus sign and a series of dot-separated identifiers immediately following the minor or pre-release version. Identifiers MUST comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers MUST NOT be empty. Build metadata SHOULD be ignored when determining version precedence. Thus two versions that differ only in the build metadata, have the same precedence.<br>
Examples: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
11. Precedence refers to how versions are compared when ordered. Precedence MUST be calculated by separating the version into the human, major, minor, and pre-release identifiers in that order (Build metadata does not figure into precedence). Precedence is determined by the first difference when comparing each of these identifiers from left to right as follows: Human, major, and minor versions are always compared numerically.<br>
Example: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1.<br>
When human, major, and minor are equal, a pre-release version has lower precedence than a normal version.<br>
Example: 1.0.0-alpha < 1.0.0.<br>
Precedence for two pre-release versions with the same human, major, and minor version MUST be determined by comparing each dot separated identifier from left to right until a difference is found as follows: identifiers consisting of only digits are compared numerically and identifiers with letters or hyphens are compared lexically in ASCII sort order. Numeric identifiers always have lower precedence than non-numeric identifiers. A larger set of pre-release fields has a higher precedence than a smaller set if all of the preceding identifiers are equal.<br>
Example: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

About
-----

The Romantic Versioning specification was authored by [Daniel V from the Legacy Blog crew](http://blog.legacyteam.info/2015/12/romver-romantic-versioning/) in 2015. This open and public repository has the task of maintenance and visibility, cooperation with others.

If you'd like to leave feedback, please [open an issue on
GitHub](https://github.com/romversioning/romver/issues).


License
-------

Creative Commons - CC BY 4.0
[http://creativecommons.org/licenses/by/3.0/](https://creativecommons.org/licenses/by/4.0/)
