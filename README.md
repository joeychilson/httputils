# httputils

A library of helper functions for Go's `net/http` package.

## Installation

```bash
go get github.com/joeychilon/httputils
```

## Usage

### Query Parameters

The library provides functions for parsing query parameters in HTTP requests:

- `QueryString(r *http.Request, key string) string`: returns a string value for a query parameter.
- `QueryStrings(r *http.Request, key string) []string`: returns a slice of strings for a query parameter.
- `QueryInt(r *http.Request, key string) int`: returns an int value for a query parameter.
- `QueryInts(r *http.Request, key string) []int`: returns a slice of ints for a query parameter.
- `QueryBool(r *http.Request, key string) bool`: returns a bool value for a query parameter.

Here's an example of how to use these functions:

```go
func myHandler(w http.ResponseWriter, r *http.Request) {
    // Get a string query parameter
    // key=foo => name = "foo"
    name := httputils.QueryString(r, "name")

    // Get a slice of strings query parameter
    // key=foo,bar => names = ["foo", "bar"]
    names := httputils.QueryStrings(r, "names")

    // Get an int query parameter
    // key=1 => id = 1
    id := httputils.QueryInt(r, "id")

    // Get a slice of ints query parameter
    // key=1,2,3 => ids = [1, 2, 3]
    ids := httputils.QueryInts(r, "ids")

    // Get a bool query parameter
    // key=true => enabled = true
    enabled := httputils.QueryBool(r, "enabled")
}
```

### JSON Responses

The library provides a function for writing JSON responses to the `http.ResponseWriter`:

`WriteJSON(w http.ResponseWriter, statusCode int, data any)`: writes a JSON response with the given status code and data.

Here's an example of how to use this function:

```go
func myHandler(w http.ResponseWriter, r *http.Request) {
    // Get some data...
    data := getSomeData()

    // Write a JSON response
    httputils.WriteJSON(w, http.StatusOK, data)
}
```
