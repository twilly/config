你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
# :fishing_pole_and_fish: config [![GoDoc][doc-img]][doc] [![Build Status][ci-img]][ci] [![Coverage Status][cov-img]][cov]

Convenient, injection-friendly YAML configuration.

## Installation

```
go get -u go.uber.org/config
```

Note that config only supports the two most recent minor versions of Go.

## Quick Start

```golang
// Model your application's configuration using a Go struct.
type cfg struct {
    Parameter string
}

// Two sources of configuration to merge.
base := strings.NewReader("module: {parameter: foo}")
override := strings.NewReader("module: {parameter: bar}")

// Merge the two sources into a Provider. Later sources are higher-priority.
// See the top-level package documentation for details on the merging logic.
provider, err := config.NewYAML(config.Source(base), config.Source(override))
if err != nil {
    panic(err) // handle error
}

var c cfg
if err := provider.Get("module").Populate(&c); err != nil {
  panic(err) // handle error
}

fmt.Printf("%+v\n", c)
// Output:
// {Parameter:bar}
```

## Development Status: Stable

All APIs are finalized, and no breaking changes will be made in the 1.x series
of releases. Users of semver-aware dependency management systems should pin
config to `^1`.

---

Released under the [MIT License](LICENSE.txt).

[doc-img]: http://img.shields.io/badge/GoDoc-Reference-blue.svg
[doc]: https://godoc.org/go.uber.org/config

[ci-img]: https://img.shields.io/travis/uber-go/config/master.svg
[ci]: https://travis-ci.org/uber-go/config/branches

[cov-img]: https://codecov.io/gh/uber-go/config/branch/master/graph/badge.svg
[cov]: https://codecov.io/gh/uber-go/config/branch/master
