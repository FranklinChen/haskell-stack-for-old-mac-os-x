# Haskell Stack binary for old Mac OS X

[![Build Status](https://travis-ci.org/FranklinChen/haskell-stack-for-old-mac-os-x.png)](https://travis-ci.org/FranklinChen/haskell-stack-for-old-mac-os-x)

I still have (not as my main machine of course) an old [early 2008 black MacBook](http://www.everymac.com/systems/apple/macbook/specs/macbook-core-2-duo-2.4-black-13-early-2008-penryn-specs.html) which is running Mac OS X 10.7.5, and cannot be upgraded beyond that.

Haskell Stack is not supported for this machine and no binary for it is available, so I have to build it from source using just Cabal, then use the binary to bootstrap further builds. Once bootstrapped, building newer versions is simple. For example, upgrading to Stack 1.0.0 required:

```console
$ stack unpack stack-1.0.0
$ cd stack-1.0.0
$ stack install --flag cryptonite:-support_aesni
```

This works around the following:

- https://github.com/commercialhaskell/stack/issues/1477
- https://github.com/haskell-crypto/cryptonite/issues/21
- https://github.com/haskell-crypto/cryptonite/issues/27
