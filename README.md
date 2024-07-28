## Golang Password Generator

[![GoDoc](https://img.shields.io/badge/go-documentation-blue.svg?style=flat-square)](https://pkg.go.dev/github.com/juev/go-password/password)
[![Test](https://github.com/juev/go-password/actions/workflows/test.yml/badge.svg)](https://github.com/juev/go-password/actions/workflows/test.yml)

<hr>

This is a fork of the [sethvargo/go-password](https://github.com/sethvargo/go-password) repository, which has made 
changes that, in my  opinion, make the library safer and easier to  use. But since the main developer did not accept 
these changes, so as  not to break the established API, I created this fork.

<hr>

This library implements generation of random passwords with provided
requirements as described by  [AgileBits
1Password](https://discussions.agilebits.com/discussion/23842/how-random-are-the-generated-passwords)
in pure Golang. The algorithm is commonly used when generating website
passwords.

The library uses crypto/rand for added randomness.

Sample example passwords this library may generate:

```text
0N[k9PhDqmmfaO`p_XHjVv`HTq|zsH4XiH8umjg9JAGJ#\Qm6lZ,28XF4{X?3sHj
7@90|0H7!4p\,c<!32:)0.9N
UlYuRtgqyWEivlXnLeBpZvIQ
Q795Im1VR5h363s48oZGaLDa
wpvbxlsc
```

> Since these are completely randomized, it's possible that they may generate passwords that don't comply with some custom password policies, such as ones that require both upper case AND lower case letters. If your particular use case needs a mix of casing, then you can either increase the number of characters in the password or check the output and regenerate if it fails a particular constraint, such as requiring both upper and lower case.

## Installation

```sh
$ go get -u github.com/juev/go-password/password
```

## Usage

```golang
package main

import (
  "log"

  "github.com/juev/go-password/password"
)

func main() {
  // Generate a password that is 64 characters long with 10 digits, 10 symbols,
  // allowing upper and lower case letters, disallowing repeat characters.
  res, err := password.Generate(password.Input{
	  Length:  64,
	  Digits:  10,
	  Symbols: 10,
  })
  if err != nil {
    log.Fatal(err)
  }
  log.Printf(res)
}
```

See the [GoDoc](https://godoc.org/github.com/juev/go-password) for more
information.

## License

This code is licensed under the MIT license.
