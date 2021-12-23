# Connectom
A simple DSL for architects

Connectom is a (from scratch) try to design and implement a (bootstrapping) domain specific language for developing (enterprise) architecture.

Instead of providing a architecture schema based on an existing framework (like Togaf or Cobit) it should be as generic as possible by providing an abstract schema and methods to create (and manipulate) levels, groups, elements, and there connections. Methods of Connectom should be accessable via a CLI on the first hand and later on via API. Views are out of scope for the core functionality but should be able to implemeted via plug-ins.

The Connectom DSL have to handle and provide trees, there elements(leafs), references as istances and references as connections. To be generic it needs to handle schema classifications of the elements.

### Example:

```
tree
  element schema:type
    element schema:type connection:element
      element  schema:type
    element schema:type
  element schema:type
schema
  type:description
  type:description
```

On the lowest level the DSL needs to support three domains of manipulating the architecture: handle the tree, there connections and the schema itself:

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

(Remark: alter existing elements, connections, or attributes are series of these atomic functions provided as transactions.)  

### Example:

