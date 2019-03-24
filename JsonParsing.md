## JSON Parsing
bool, for JSON booleans
float64, for JSON numbers
string, for JSON strings
[]interface{}, for JSON arrays
map[string]interface{}, for JSON objects
nil for JSON null

The defaults that the json package will decode into when the type isn't declared are:

bool, for JSON booleans
float64, for JSON numbers
string, for JSON strings
[]interface{}, for JSON arrays
map[string]interface{}, for JSON objects
nil for JSON null
Since each record is (in your example) a json object, you can assert each one as a map[string]interface{} like so:

```go
for _, record := range view {
    log.Printf(" [===>] Record: %s", record)

    if rec, ok := record.(map[string]interface{}); ok {
        for key, val := range rec {
            log.Printf(" [========>] %s = %s", key, val)
        }
    } else {
        fmt.Printf("record not a map[string]interface{}: %v\n", record)
    }
}
```
