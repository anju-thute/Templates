# EXCEADS-Templates
Templates for inclusion in EXCEADS

Repository directory organization:
* Type of Template
  - Instance of Template
    - JSON file
    - Documentation in Markdown
    - PNG or other "cartoon" of template (optional)
* dev
  - Similar to the above structure for development of new templates

## Contents
#### Disease
* [SEIR](https://github.com/NSSAC/EXCEADS-Templates/blob/master/disease/seir/seir.md)
* [Ebola](https://github.com/NSSAC/EXCEADS-Templates/blob/master/disease/ebola/ebola.md)

    
## Documentation of the EXCEADS specific tags
Documentation of the "exceads" specific tags in the templates

```
  "exceads": {
    "requires": {
      "allOf": ["diseaseModelTemplate1.json"]
    }
  }
```
Explicit dependency of the template on existence of other templates (through filename for now)

More examples here please!
