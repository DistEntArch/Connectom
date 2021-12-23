# Connectom
A simple DSL for architects

Connectom is a (from scratch) try to design and implement a (bootstrapping) domain specific language for developing (enterprise) architecture.

Instead of providing a architecture schema based on an existing framework (like Togaf or Cobit) it should be as generic as possible by providing an abstract schema and methods to create (and manipulate) levels, groups, elements, and there connections. Methods of Connectom should be accessable via a CLI on the first hand and later on via API. Views are out of scope for the core functionality but should be able to implemeted via plug-ins.

The Connectom DSL have to handle and provide elements, references as tree graph, references as istances and references as connections. To be generic it needs to handle schema classifications of the elements.

### Example:

```
elements 
  element schema:type
  element schema:type
  element schema:type
  …
tree
  element ref:element
    element ref:element ref:connection
      element ref:element ref:connection
    element ref:element
  element ref:element ref:connection
  
schema
  type:description
  type:description
```

On the lowest level the DSL needs to support three domains of manipulating the architecture: handle the tree, there connections and the schema itself:

Element methods:
  - add
  - delete

Tree methods:
  - add
  - delete
  - add attribute 
  - delete attribute

Connection methods:
  - add
  - delete
  - add attribute 
  - delete attribute

Schema methods:
  - add
  - delete

(Note: All functions provided nativly are atomic. Higher order functions like move or change schema can be impmented as transactions similar to Forth words.)  

### Example:

```
a1 = Architecture()
a1.import.schema('schema.txt')                         # keyword 'Tools' is defined as list of 'Tool' which is a simple element type
a1.add.element({'Tools':['Spark','Python','R','Lambda']})       # keyword 'Tools' is defined as list of 'Tool' which is a simple element type
a1.add.element({'Storage':'S3'})
a1.add.element({'Platform':'CDP DataHub'})
a1.group.elements({'CDP Data Computation':['Spark','Python','R']})
a1.add.connection({'API call':'get'})
a1.add.connection({'Data Segmentation':['Master Data','Metadata','Event Data','Tracingdata']})
a1.connect({'CDP Data Computation':'S3'},'get','Master Data')
