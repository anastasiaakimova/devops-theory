# Python for scripting ( loop, conditional, vars, functions )

## Variables (basics)
Python variables are dynamically typed (no type declaration).
```
name = "Anastasia"
age = 25
is_active = True
pi = 3.14
```
|||
|---|---|
|text = "hello"          |str|
count = 10               |int|
load = 0.75              |float|
enabled = False          |bool|
items = ["a", "b"]       |list|
config = {"env": "dev"}  |dict|


## Conditionals (if / elif / else)
```
env = "prod"

if env == "prod":
    print("Production mode")
elif env == "dev":
    print("Development mode")
else:
    print("Unknown environment")
```

### Operators

```
==   !=   >   <   >=   <= 
and  or   not
```

Example (very common in scripts):
```
cpu = 85
if cpu > 80 and cpu < 95:
    print("High CPU usage")
```

## Loops

### for loop (most common)
```
services = ["nginx", "redis", "postgres"]

for service in services:
    print(service)
```

With index:
```
for i, service in enumerate(services):
    print(i, service)
```
Range:
```
for i in range(5):
    print(i)
```

### while loop
```
count = 0

while count < 3:
    print(count)
    count += 1
```

## Functions
### Basic function
```
def greet(name):
    print(f"Hello, {name}")
greet("Anastasia")
```

### Return value
```
def add(a, b):
    return a + b
result = add(2, 3)
print(result)
```
