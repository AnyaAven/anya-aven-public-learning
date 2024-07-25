# YAML

---

YAML is a popular format for configuration files.

YAML is a data serialization language, same as XML and JSON.

It stands for "YAML Ain't Markup Language", *cough cough*, recursion!

---
Here is the difference between YAML, XML, and JSON:
### YAML
>YAML is superset of JSON: any valid JSON file is also a valid YAML file
```yaml
microservices:
  - app: user-authentication
    port: 9000
    version: 1:00 # Here's a comment
    boolean: yes
```
### XML
```xml
<microservices>

    <app>user-authentication</app>
    <port>900</port>
    <version>1.0</version>
    
</microservices> <!-- Here's a comment-->
```
### JSON
```json
{
  "microservices": [
    {
      "app": "user-authentication", 
      "port": 9000,
      "version": "1.0"
    }
  ]
}
```
## Notices

---
- XML uses `< >` and JSON uses `{ }` but YAML uses indentation.
- Strings don't need `""` in YAML
- Can comment (JSON does not have comments)
- microservices is an object
- The hyphen makes `app` a list
- Valid booleans: true, false, on, off, yes, no

## Special Cases

---
## Multi Lined or Long Strings

```yaml
multilineString: 
  linebreaks: | 
    this is a single line string,
    that cares about line breaks.

  longString: > 
    this is a single line strings 
    that doesn't save line breaks 
```

## Placeholders

```yaml
metadata:
    name: {{ .Values.service.name }}
```

## Separate Components in a single file

```yaml
config1:
  name: one

--- # This separates the 2 components

config2:
  name: one
```