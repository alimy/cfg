### cfg
[![Go](https://github.com/alimy/cfg/actions/workflows/go.yml/badge.svg)](https://github.com/alimy/cfg/actions/workflows/go.yml)
[![GoDoc](https://godoc.org/github.com/alimy/cfg?status.svg)](https://pkg.go.dev/github.com/alimy/cfg)
[![Sourcegraph](https://img.shields.io/badge/view%20on-Sourcegraph-brightgreen.svg?logo=sourcegraph)](https://sourcegraph.com/github.com/alimy/cfg)

A flexible features configure help library

### Usage
```go
package main

import(
    "fmt"

    "github.com/alimy/cfg"
)

func main() {
    suites := map[string][]string{
		"default": {"Sms", "Alipay", "Zinc", "MySQL", "Redis", "AliOSS", "LogZinc"},
		"develop": {"Zinc", "MySQL", "AliOSS", "LogFile"},
		"slim":    {"Zinc", "MySQL", "Redis", "AliOSS", "LogFile"},
	}
	kv := map[string]string{
		"sms": "SmsJuhe",
	}

    // initialize cfg
	cfg.Initial(suites, kv)

    if cfg.If("Alipay") {
        fmt.Println("use Alipay feature")
    }

    if cfg.If("Sms") {
        sms := cfg.As("Sms")
        fmt.Println("use Sms feature and the value is %s", sms)
    }
}
```