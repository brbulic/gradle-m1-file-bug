# gradle-m1-file-bug
Gradle bug with gradle 5.0 and ARM64e java with creating files

## Guide to test
1. On your M1 Mac (M1/M1 Pro/M1 Max) install JDK 11 which supports ARM64e (either from [Homebrew](https://formulae.brew.sh/formula/openjdk@11) or [Azul](https://cdn.azul.com/zulu/bin/zulu11.52.13-ca-jdk11.0.13-macosx_aarch64.dmg))
1.  Run `./gradlew makeFile`

### Expected results
You should have a file in `./build/files/testFile.txt` with some jibberish. That means it works

### What actually happens on M1 Macs with ARM64E JDK distribution
An exception and no file.

Googling didn't find any problem, exepct that M1 Macs (Apple Sillicon) is officially supported from Gradle 7.0 and up. Since some development workflows still depend on earlier versions of gradle (because legacy code), this means that M1 Macs must continue using x64 distributions of JDK via rosetta which kind of defeats the purpouse of the new, fast and efficient M1 chips.

So we must either spend lots of engineer hours to bring our projects to latest spec because of developer ergonomics or just use Rosetta.
