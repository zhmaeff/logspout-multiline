# logspout-multiline

## This repo becomes deprecated with the merge of [PR](https://github.com/gliderlabs/logspout/pull/370/files) in official [repo](https://github.com/gliderlabs/logspout)

#### Usage
Follow the instructions in [Custom folder](https://github.com/gliderlabs/logspout/tree/master/custom) on how to build your own Logspout container with custom modules. Basically just copy the contents of the custom folder and include:

```go
package main

import (
	_ "github.com/zhmaeff/logspout-multiline"
	_ "github.com/looplab/logspout-logstash"
	_ "github.com/gliderlabs/logspout/transports/tcp"
	_ "github.com/gliderlabs/logspout/transports/udp"
)
```
in `modules.go`.

#### Environment variables
* `MULTILINE_ENABLE_DEFAULT` - enable multiline logging for all containers (default `true`)
* `MULTILINE_MATCH` - determines which lines the pattern should match, one of first|last|nonfirst|nonlast (default `nonfirst`)
* `MULTILINE_PATTERN` - pattern for multiline logging, see: MULTILINE_MATCH (default: `^\s`)
* `MULTILINE_FLUSH_AFTER` - maximum time between the first and last lines of a multiline log entry in milliseconds (default: 500)
