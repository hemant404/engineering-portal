---
title: "What is the New in the golang1.15| LoginRadius"
date: "2020-08-20"
coverImage: "index.png"
author: "Vijay Singh Shekhawat"
tags: ["Go", "golang","Go 1.15", "Go Features", "Go Improvement", "Go Package", "Go New Features"]
---


Go announce [Go 1.15](https://blog.golang.org/) released on 11 Aug 2020. Highlighted updates and features include Substantial improvements to the Go linker, Improved allocation for small objects at high core counts, X.509 CommonName deprecation, GOPROXY supports skipping proxies that return errors, New embedded tzdata package, Several Core Library improvements and more. 

As [Go promise](https://golang.org/doc/go1compat) for maintaining backward compatibility. After upgrading to the latest Go 1.15 version almost all existing Go lang applications or programs continue to compile and run as older Go lang version.

You can download the latest Go Version from the [Download] (https://golang.org/dl/) page.


### Operating system and platform compatibility

#### macOS
Go 1.14 version announced some changes for the macOS. According to announcement  

> Go 1.14 is the last release that will run on macOS 10.11 El Capitan. Go 1.15 will require macOS 10.12 Sierra or later.

The lastest macOS 10.15 (Catalina) is no longer supporting 32-bit binaries. Go 1.14 will likely be the last Go release to support 32-bit binaries on iOS, iPadOS, watchOS, and tvOS (the darwin/arm port). Go continues to support the 64-bit darwin/amd64 port.


#### Windows

Go now generates Windows ASLR executables when -buildmode=pie cmd/link flag is provided. Go command uses `-buildmode=pie` by default on Windows.

The -race and -msan flags now always enable `-d=checkptr`, which checks uses of unsafe. Pointer. This was previously the case on all OSes except Windows.

#### Andiord

Mobile applications were crashing in some devices due to some invalid lld linker versions so now avoiding the crashing the latest Go 1.15 version explicitly selects the lld linker available in recent versions of the NDK. This explicitly lld linker avoids crashes on some devices. it becomes the default NDK linker in a future NDK version.


### Smaller binaries & Performance improvements 
Always new Go 1.15 brings many minor performance improvements. The first major improvement has reduced the executable's binary size by almost 5% - 10% as compared to Go 1.14. As Brad Fitzpatrick [tweet](https://twitter.com/bradfitz/status/1256348714198654976?lang=en), test program down from 8.2MB in Go 1.14 to 3.9MB in 1.15. 

![image 1](lr-tweet1.png)

![image 1](lr-tweet2.png)

Go 1.15 has improved the code build process now unused code is eliminating in the new linker, along with several targeted improvements, such as Clements's CL 230544, which reduces the number of stack and register maps included in the executable.  

### Standard library additions
Always in every new version release Go come with various minor changes and updates to the library. I m including some useful and important changes  

#### tzdata Package
A new embedded tzdata package was added that permits embedding the timezone database into a program. Importing this package (as import _ "time/tzdata") which allows the program to find timezone information without the timezone database is not available on the local system. You can also embed the timezone database by building with -tags timet/zdata. This approach increases the size of the program by about 800 KB. This might be useful if you want to test some code with the virtualized environments like Go playground.

#### X.509 CommonName deprecation
The standard library's testing package is quite minimalist — the Go philosophy is to avoid domain-specific languages for writing tests and assertions, and instead to just write plain Go, which the developer already knows. But the core developers found creating a temporary directory useful enough to approve adding a TempDir() method that lazily creates a temporary directory for the current test and deletes it automatically when the test is finished.

#### net/url Package
The `net/url` package adds a new URL. The redacted () method that returns the URL as a string. This is proposed in the [34855](https://github.com/golang/go/issues/34855). It is a very useful improvement for audit logging and security. It's a simple derivation from the URL.String() that masks the password if exists from the string being passed. It does not modify at all to the URL itself but a copy of it.

### Summary
Go 1.15 have released with various improvements, bug fixes. You can get all improvements, closed proposals and features details for the Go GitHub repository


### Referance 
- [Go Blog]("https://blog.golang.org/")
- [Go 1.15]("https://golang.org/doc/go1.15")

