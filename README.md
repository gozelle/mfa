This is a Go implementation of the Google Authenticator library.

[![GoDoc](https://godoc.org/github.com/dgryski/dgoogauth?status.svg)](https://godoc.org/github.com/dgryski/dgoogauth) [![Build Status](https://travis-ci.org/dgryski/dgoogauth.png)](https://travis-ci.org/dgryski/dgoogauth)

Copyright (c) 2012 Damian Gryski <damian@gryski.com>
This code is licensed under the Apache License, version 2.0

It implements the one-time-password algorithms specified in:

* RFC 4226 (HOTP: An HMAC-Based One-Time Password Algorithm)
* RFC 6238 (TOTP: Time-Based One-Time Password Algorithm)

You can learn more about the Google Authenticator library at its project page:

* https://github.com/google/google-authenticator

## 上手使用

```go
package main

func main() {
	var otp OTPConfig
	
	otp.Secret = "2SH3V3GDW7ZNMGYE"  // 请注意开始
	otp.WindowSize = 1
	
	uri := otp.ProvisionURIWithIssuer("user", "issuer")
	_ = uri  // 生成二维码地址
	
	
	ok,err := otp.Authenticate("324592") 
	if err != nil || !ok{
		// 验证码错误
    }
}
```