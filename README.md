# Godzippa!

[![Build Status][build status badge]][build status]
[![License][license badge]][license]
[![Swift Version][swift version badge]][swift version]
![Cocoapods platforms][cocoapods platforms badge]
[![Cocoapods compatible][cocoapods badge]][cocoapods]
[![Carthage compatible][carthage badge]][carthage]

**gzip Compression / Decompression Category for NSData & NSFileManager**

## Example Usage

### Objective-C

#### NSData

```objective-c
NSData *originalData = [@"Look out! It's..." dataUsingEncoding:NSUTF8StringEncoding];
NSData *compressedData = [originalData dataByGZipCompressingWithError:nil];
NSData *decompressedData = [compressedData dataByGZipDecompressingDataWithError:nil];
NSLog(@"%@ %@", [NSString stringWithUTF8String:[decompressedData bytes]], @"Godzippa!");
```

#### NSFileManager

```objective-c
NSFileManager *fileManager = [NSFileManager defaultManager];
NSURL *file = [NSURL fileURLWithPath:@"/path/to/file.txt"];
NSError *error = nil;

[fileManager GZipCompressFile:file
        writingContentsToFile:[file URLByAppendingPathExtension:@"gz"]
                        error:&error];
```

### Swift

#### NSData

```swift
let originalString = "Look out! It's Godzippa!"
let originalData = originalString.data(using: .utf8)! as NSData
let compressedData = try! originalData.gzipCompressed() as NSData
let decompressedData = try! compressedData.gzipDecompressed()
let decompressedString = String(data: decompressedData, encoding: .utf8)
```

#### FileManager

```swift
let fileManager = FileManager.default
let textFile = URL(fileURLWithPath: "/path/to/file.txt")
let gzipFile = textFile.appendingPathExtension("gz")
try fileManager.gzipCompressFile(at: textFile, to: gzipFile)
```

## Requirements

- **zlib** - In the "Link Binary With Libraries" Build Phase of your Target, add `libz.dylib`

## Contact

Mattt ([@mattt](http://twitter.com/mattt))

## License

Godzippa! is available under the MIT license.
See the LICENSE file for more info.

[build status]: https://travis-ci.org/mattt/Godzippa
[build status badge]: https://api.travis-ci.org/mattt/Godzippa.svg?branch=master
[license]: https://opensource.org/licenses/MIT
[license badge]: https://img.shields.io/cocoapods/l/Godzippa.svg
[swift version]: https://swift.org/download/
[swift version badge]: https://img.shields.io/badge/swift%20version-4.0+-orange.svg
[cocoapods platforms badge]: https://img.shields.io/cocoapods/p/Godzippa.svg
[cocoapods]: https://cocoapods.org/pods/Godzippa
[cocoapods badge]: https://img.shields.io/cocoapods/v/Godzippa.svg
[carthage]: https://github.com/Carthage/Carthage
[carthage badge]: https://img.shields.io/badge/Carthage-compatible-4BC51D.svg
