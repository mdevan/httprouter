
This is a fork of [github.com/julienschmidt/httprouter](https://github.com/julienschmidt/httprouter),
with one single, API-breaking change: the handler functions are of the type
`http.HandlerFunc` rather than `httprouter.Handle`.

This is how a handler function would be defined in the original `httprouter`:

```go
import "github.com/julienschmidt/httprouter"

func Hello(w http.ResponseWriter, r *http.Request, ps httprouter.Params) {
    fmt.Fprintf(w, "hello, %s!\n", ps.ByName("name"))
}
```

And here is the same in the new one:

```go
import "github.com/mdevan/httprouter"

func Hello(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "hello, %s!\n", httprouter.Param(r, "name"))
}
```

Under the hood, the params are stored in the context attached to http.Request.

There are no other changes.

For docs and everything else, please refer https://github.com/julienschmidt/httprouter.
The auto-generated API doc is available at http://godoc.org/github.com/mdevan/httprouter.



