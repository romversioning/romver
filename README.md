# Romantic Versioning (RomVer)

## Spec Summary

![Diagram with a version number: 2.25.123
First "2" is commented: Project
Second "25" is commented: Major
Third "123" is commented: Minor](./romvers.png)

---

Version numbers are defined as `PROJECT.MAJOR.MINOR`, where you increment the:

1. `PROJECT` segment when you want the version to be considered a new, separate project (e.g. Sdl 2.28 to Sdl 3.0).
2. `MAJOR` segment when you make breaking changes.
3. `MINOR` segment when you make non-breaking changes (e.g. adding functionality or bug fixes in a backward-compatible manner).

Additional labels for pre-release and build metadata are available as extensions to the PROJECT . MAJOR . MINOR format.

## Introduction

This is an alternative to the [SemVer](https://semver.org/) format, focusing instead on defining and standardizing version numbers based off the ways in which people naturally treat them. Many large and popular projects (e.g. Node, Rails, PHP, jQuery, NPM, the Linux Kernel, and many more) deny using SemVer and instead opt to just base their versions off intuition. RomVer acknowledges the importance of this intuition and attempts to standardize version numbers in a way that is both extremely intuitive and extremely useful.

The Romantic Versioning specification was originally authored by [Daniel V](https://web.archive.org/web/20221003075344/http://blog.legacyteam.info/2015/12/romver-romantic-versioning/) in 2015, and this open and public repository has the task of maintaining, extending, polishing, and popularizing this standard. If you'd like to leave feedback, please [open an issue on GitHub](https://github.com/romversioning/romver/issues).

## Why was this made?

This was made to fix the confusion that SemVer often creates regarding MAJOR changes. When a project releases a v2.0, people don't automatically think of it as a simple breaking change as they should, they think of it as being an extremely big deal. And conversely, when a project releases a v54.0, people don't automatically think of it as a simple breaking change as they should, they think of it as another small and tedious step that isn't noteworthy.

For whatever reason, humans seem to naturally put a lot of personal attachment in the first number of a version, and this standard attempts to work with that fact instead of overriding it. 

## Why should this be used?

- Users (including developers) are less confused and are quicker to pick up on the importance of version changes (as described above).
- It conveys more information to users
- - The MINOR and PATCH segments in SemVer are both backwards-compatible, so they're identical when it comes to whether or not users should update. Here, they're combined into a single segment.
- - The PROJECT and MAJOR segments denote differing levels of breaking changes, with MAJOR increments likely being easy to update to and PROJECT increments likely being not easy to update to.
- It is compatible with systems that expect SemVer.
- (Extra) The specification is barely even needed since it basically just states what people already expect when looking at the three numbers.
- (Extra) You don't have to do something crazy like "Project v2 v0.1.0" if you want to radically transform your project.

## Links
* [License](https://creativecommons.org/licenses/by/4.0/)
* [FAQ](FAQ.md)
* [Contributing](CONTRIBUTING.md)
* [Code of Conduct](CODE_OF_CONDUCT.md)

## Romantic Versioning Specification

If a software project wishes to use Romantic Versioning, it must follow these rules:
1. Version numbers must take the form `PROJECT.MAJOR.MINOR[-PRE][+BUILD]` where PROJECT, MAJOR, and MINOR are non-negative integers with no leading zeroes, and PRE and BUILD are optional identifiers composed only of ASCII alphanumerics, hyphens, and dots.
2. Once a release of the project is publicly available, its contents must never be modified. Any necessary modifications must be issued as a new release.
3. If a release contains a public API, said API must be precisely and comprehensively documented.
4. Project version zero (0.*.*) must be used for initial development, where the project is marked as not stable.
5. Each release's version number must be based off its predecessor's version number and must be changed according to the next three rules.
6. If the release is to be considered as a separate project from older releases, or if the project is now marked as stable, the PROJECT identifier must be incremented and the MAJOR and MINOR identifiers must be set to 0.
7. Otherwise, if the release is not backwards compatible with its predecessor, or if some of the release's public API is now marked as deprecated, the MAJOR identifier must be incremented and the MINOR identifier must be set to 0.
8. Otherwise, the MINOR identifier must be incremented.
9. A pre-release version may be denoted by appending immediately following the MINOR identifier a hyphen and any ASCII string composed only of alphanumerics, dots, and hyphens. Pre-release identifiers, if included, must not be empty, and pre-release version numbers must only be issued for releases which are unstable previews for future releases.<br>
Examples: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.
10. Build metadata may be denoted by appending immediately following the pre-release identifier (or otherwise the MINOR identifier) a plus sign and any ASCII string composed only of alphanumerics, dots, and hyphens. Build metadata identifiers, if included, must not be empty, and version numbers containing build metadata must only be issued for copies of the software project included within a release, and not for a release itself.<br>
Examples: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.
11. Precedence refers to how versions are compared when ordered, which must be computed by comparing the PROJECT identifiers if they differ, otherwise by comparing the MAJOR identifiers if the differ, otherwise by comparing the MINOR identifiers if they differ, otherwise by comparing the release dates of the pre-release identifiers if they differ, otherwise the version numbers are considered identical. The presence (or lack thereof) of build metadata identifiers does not affect precedence, and pre-release version numbers have lower precedence than non-pre-release version numbers.<br>
Example: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1 < 2.1.2-rc.1 < 2.1.2-rc2 < 2.1.2.<br>

## License

[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)
