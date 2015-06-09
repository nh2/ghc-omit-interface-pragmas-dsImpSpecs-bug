# ghc-omit-interface-pragmas-dsImpSpecs-bug

Repro for GHC 7.8.4 panic: dsImpSpecs on SPECIALISE pragma with -fhpc enabled


## How to reproduce

Run `cabal build --ghc-options "-fhpc"`.

Output:

```
Package has never been configured. Configuring with default flags. If this
fails, please run configure manually.
Resolving dependencies...
Configuring ghc-omit-interface-pragmas-dsImpSpecs-bug-0.1.0.0...
Building ghc-omit-interface-pragmas-dsImpSpecs-bug-0.1.0.0...
Preprocessing library ghc-omit-interface-pragmas-dsImpSpecs-bug-0.1.0.0...
[1 of 2] Compiling A                ( src/A.hs, dist/build/A.o )
[2 of 2] Compiling B                ( src/B.hs, dist/build/B.o )

src/B.hs:5:1: Warning:
    SPECIALISE pragma for non-overloaded function ‘myfun’
ghc: panic! (the 'impossible' happened)
  (GHC version 7.8.4 for x86_64-unknown-linux):
	dsImpSpecs
    ghc-omit-interface-pragmas-dsImpSpecs-bug-0.1.0.0:A.myfun{v rpu} [gid]

Please report this as a GHC bug:  http://www.haskell.org/ghc/reportabug
```

```
$ ghc --version
The Glorious Glasgow Haskell Compilation System, version 7.8.4
```

```
$ cabal --version
cabal-install version 1.18.0.8
using version 1.18.1.5 of the Cabal library 
```
