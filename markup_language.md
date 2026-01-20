# Markup language (YAML, xml, json)

These languages are not programming languages.
 They are used to:
- Describe **data structure**
- Store **configuration**
- Exchange data between systems
- Represent **hierarchies** (key → value, parent → child)


They **don’t contain logic** (no loops, conditions, functions).


## Json (JavaScript Object Notation)

What it looks like
```
{
  "app": "nginx",
  "replicas": 3,
  "ports": [80, 443],
  "enabled": true
}
```
### Key characteristics
- Key-value pairs
- Uses {} and []
- Strict syntax
- Keys must be strings
- No comments allowed
### Data types
- string
- number
- boolean
- null
- array
- object
### Where JSON is used
- REST APIs (request / response bodies)
- Configuration files
- AWS APIs
- Docker, Terraform outputs
- Web applications

✅ Simple <br>
✅ Easy to parse <br>
❌ No comments <br>


## YAML (YAML Ain’t Markup Language)

What it looks like
```
app: nginx
replicas: 3
ports:
  - 80
  - 443
enabled: true
```
### Key characteristics
- Uses indentation, not brackets
- Human-readable
- Supports comments
- Sensitive to spaces
### Data types
- string
- number
- boolean
- null
- list
- map (dictionary)
### Where YAML is used
- Kubernetes manifests
- Helm charts
- Ansible playbooks
- GitLab CI / GitHub Actions
- Docker Compose

❌ Parsing is more complex <br>


## XML (eXtensible Markup Language)


What it looks like
```
<app>
  <name>nginx</name>
  <replicas>3</replicas>
  <ports>
    <port>80</port>
    <port>443</port>
  </ports>
</app>
```

### Key characteristics
- Tag-based
- Opening and closing tags
- Strong structure
### Where XML is used
- SOAP APIs
- Legacy systems
- Configuration files (older tools)
- Java ecosystems (Spring, Maven POM)

✅ Very strict <br>
✅ Good for complex documents <br>
❌ Less popular in modern DevOps <br>
