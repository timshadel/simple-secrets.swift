# simple-secrets.swift [![Build Status](https://travis-ci.org/timshadel/simple-secrets.swift.png?branch=master)](https://travis-ci.org/timshadel/simple-secrets.swift)

The Swift implementation of a simple, opinionated library for encrypting small packets of data securely. Designed for exchanging tokens among systems written in a variety of programming languages:

- [Node.js](https://github.com/timshadel/simple-secrets)
- [Ruby](https://github.com/timshadel/simple-secrets.rb)
- [Rust](https://github.com/timshadel/simple-secrets.rs)
- [Swift](https://github.com/timshadel/simple-secrets.swift)
- [Objective-C](https://github.com/timshadel/SimpleSecrets)
- [Java](https://github.com/timshadel/simple-secrets.java)
- [Erlang](https://github.com/CamShaft/simple_secrets.erl)

## Examples

### Basic

Send:

```swift
import SimpleSecrets

// Try `head /dev/urandom | shasum -a 256` to make a decent 256-bit key
let sender = try Sender(hex: "<64-char hex string master key (32 bytes, 256 bits)>")
let packet = try sender.pack("this is a secret message");
// => 'Qr4m7AughkcQIRqQvlyXiB67EwHdBf5n9JD2s_Z9NpO4ksPGvLYjNbDm3HRzvFXFSpV2IqDQw_LTamndMh2c7iOQT0lSp4LstqJPAtoQklU5sb7JHYyTOuf-6W-q7W8gAnq1wCs5'
```

Receive:

```swift
import SimpleSecrets

// Same shared key
let sender = Sender(hex: "<64-char hex string master key (32 bytes, 256 bits)>")
// Read data from somewhere
let packet = "OqlG6KVMeyFYmunboS3HIXkvN_nXKTxg2yNkQydZOhvJrZvmfov54hUmkkiZCnlhzyrlwOJkbV7XnPPbqvdzZ6TsFOO5YdmxjxRksZmeIhbhLaMiDbfsOuSY1dBn_ZgtYCw-FRIM"
let packet = sender.unpack(token)
// => [ "msg" : "this is a secret message" ]
```

## Can you add ...

This implementation follows the spec for the [Node.js](https://github.com/timshadel/simple-secrets) version for 100% compatibility.
