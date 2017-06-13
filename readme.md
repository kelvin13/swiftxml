# SwiftXML

[![Build](https://travis-ci.org/kelvin13/swiftxml.svg?branch=master)](https://travis-ci.org/kelvin13/swiftxml)
[![Issues](https://img.shields.io/github/issues/kelvin13/swiftxml.svg)](https://github.com/kelvin13/swiftxml/issues?state=open)
[![Language](https://img.shields.io/badge/version-swift_4-ffa020.svg)](https://swift.org/)
[![License](https://img.shields.io/badge/license-GPL3-ff3079.svg)](https://github.com/kelvin13/swiftxml/blob/master/LICENSE.gpl3)
[![Queen](https://img.shields.io/badge/taylor-swift-e030ff.svg)](https://www.google.com/search?q=where+is+ts6&oq=where+is+ts6)

**Lightweight XML parsing in *pure* Swift 3. No Foundation. No dependencies.**

SwiftXML doesn’t wrap anything. It parses XML directly, character by character. And the API is simple and easy to use. In fact, it exposes just two objects — a protocol and a function:

```swift
protocol Parser
{
    func handle_data(data:[Unicode.Scalar], level:Int)
    func handle_starttag(name:String, namespace_uri:String?, attributes:[String: String], level:Int)
    func handle_startendtag(name:String, namespace_uri:String?, attributes:[String: String], level:Int)
    func handle_endtag(name:String, namespace_uri:String?, level:Int)
    func error(_ message:String, line:Int, column:Int)
}
```

```swift
func parse(_:String, parser:Parser)
```

SwiftXML will tokenize your XML string into tags and data. It does not build any tree structures; that is for you to implement. Nor does it read files from disk into memory; that is for the Swift standard library to implement (hint hint @ Swift standard library devs).

See the [`swiftxmlTests.swift`](https://github.com/kelvin13/swiftxml/blob/master/Tests/swiftxmlTests/swiftxmlTests.swift) file for a usage example, if you are still confused.
