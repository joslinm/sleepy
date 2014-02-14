## Sleepy

#### A RESTful framework for Go

Sleepy is a micro-framework for building RESTful APIs.

```go
package main

import (
    "net/url"
    "github.com/dougblack/sleepy"
)

type Item struct { }

func (item Item) Get(values url.Values) (int, interface{}) {
    items := []string{"item1", "item2"}
    data := map[string][]string{"items": items}
    return 200, data
}

func main() {
    item := new(Item)

    var api = sleepy.NewAPI()
    api.AddResource(item, "/items")
    api.Start(3000)
}
```

Now if we curl that endpoint:

```bash
curl localhost:3000/items
{"items": ["item1", "item2"]}
```

`sleepy` has not been officially released yet, as it is still in active
development.

## Docs

Documentation lives [here](http://godoc.org/github.com/dougblack/sleepy).

## License

`sleepy` is released under the [MIT License](http://opensource.org/licenses/MIT).


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/joslinm/sleepy/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

