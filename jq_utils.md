# How to parse json files (jq utils)

## Basic usage
Given a file data.json:
```
{
  "name": "api-service",
  "replicas": 3,
  "image": {
    "repo": "nginx",
    "tag": "1.25"
  },
  "ports": [80, 443],
  "enabled": true
}
```

### Pretty-print JSON
`jq '.' data.json`


## Read fields
### Top-level field
`jq '.name' data.json`

Output: <br>
`"api-service"`

### Nested field
`jq '.image.repo' data.json`

### Multiple fields
`jq '{name: .name, replicas: .replicas}' data.json`

## Arrays
### Access by index
`jq '.ports[0]' data.json`

### Iterate array
`jq '.ports[]' data.json`

### Length
`jq '.ports | length' data.json`

|||
|---|---|
|`jq '.' ` |            pretty print|
|`jq '.a.b' ` |         nested field|
|`jq '.arr[]' `|        iterate array|
|`jq 'select(.x==1)'`|  filter|
|`jq -r '.field'  ` |   raw output|
|`jq 'del(.field)' `|   delete|
|`jq '.a=5' `       |   update|

