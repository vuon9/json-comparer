# JSON Comparer

![Go](https://github.com/vuon9/jsoncomparer/workflows/Go/badge.svg)

A small library which can be using for compare two JSON (after it has been processed by `json.Unmarshal`).
The user-case could be a testing function.

Built with :fireworks: sounds :clock12: in the city.

Minimum requirement Go version >= 1.13

```
go get github.com/vuon9/jsoncomparer
```

# Examples

Compare two numbers
```go
err := jsoncomparer.Compare(1, 2) // not nil
err := jsoncomparer.Compare(1, 1) // nil
```

Compare two bools
```go
err := jsoncomparer.Compare(true, false) // not nil
err := jsoncomparer.Compare(true, true) // nil
```

Compare two strings
```go
err := jsoncomparer.Compare("Happy new year 2021", "This is the first day of the year") // not nil
err := jsoncomparer.Compare("Happy new year 2021", "Happy new year 2021") // nil
```

Compare two maps (equivalent to object in JSON which has been un-marshalled)
```go
var m1 interface{}
_ = json.Unmarshal([]byte(`{
    "abc": 1,
    "name": {
        "huy": "khila",
        "name": ["a", "b", "c"],
        "student": [
            {"name": "Binh", "age": 20},
            {"name": "An", "age": 20}
        ]
    }
}`), &str1)

var m2 interface{}
_ = json.Unmarshal([]byte(`{
    "abc": 1,
    "name": {
        "huy": "khila",
        "name": ["a", "b", "d"],
        "student": [
            {"name": "Binh", "age": 20},
            {"name": "An", "age": 20}
        ]
    }
}`), &str2)
err := jsoncomparer.Compare(m1, m2) // not nil
```

Compare two slices (equivalent to array in JSON which has been un-marshalled)
```go
var s1 interface{}
_ = json.Unmarshal([]byte(`[
    {"name": "Binh", "age": 20},
    {"name": "An", "age": 20}
]`), &s1)

var s2 interface{}
_ = json.Unmarshal([]byte(`[
    {"name": "Binh", "age": 20},
    {"name": "An", "age": 21}
]`), &s2)
err := jsoncomparer.Compare(s1, s2) // not nil
```

Please read more on test file to see how it work!