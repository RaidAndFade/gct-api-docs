#Javadoc

These APIs fetch data from the JAVA documentation based on the given path and return the appropriate data. Below you can find structs as well as endpoints.

---

---
## Datatypes
---
### Javadoc Type

Field | Description
--- | ---
`String` qualifiedName | the qualified path of the type
`String` name | the qualified name of the type
`String` type | the type string

---
### Javadoc Class

Field | Description
--- | ---
[`Array<Method>`](#javadoc-method)  constructors | The constructors of the class
[`Array<Type>`](#javadoc-type) interfaces | The interfaces that the class includes
`String` qualifiedName | The qualified class path
`Object` superClass | Information about the superclass. Looks like {`qualifiedName`:`String`,`name`:`String`} or empty object.
[`Array<Method>`](#javadoc-method) methods | The [methods](#javadoc-method) that the class has
`String` typeName | the type name of the class
`String` type | the type of the class, one of "Class", "Interface", or "Enum"
`String` name | the qualified class name
[`Array<Annotation>`](#javadoc-annotation) annotations | The class's [annotations](#javadoc-annotation)
`String` modifiers | The class's modifiers
[`Array<Field>`](#javadoc-field) fields | The class's [fields](#javadoc-field)

---
### Javadoc Method

Field | Description
--- | ---
`String` qualifiedName | The qualified method path
`String` name | the qualified method name
`String` docString | the method's documentation string
[`Array<Annotation>`](#javadoc-annotation) annotations | The method's [annotations](#javadoc-annotation)
`String` modifiers | The method's modifiers
[`Array<Type>`](#javadoc-type) exceptions | The methods's [exceptions](#javadoc-type)
[`Array<Parameter>`](#javadoc-parameter) parameters | The methods's [parameters](#javadoc-parameter)
_Optional_ [`Type`](#javadoc-type) returntype | the [type](#javadoc-type) of the method's return value


---
### Javadoc Field

Field | Description
--- | ---
`String` qualifiedName | The qualified field path
`String` name | the qualified field name
`String` docString | the field's documentation string
[`Array<Annotation>`](#javadoc-annotation) annotations | The field's [annotations](#javadoc-annotation)
`String` modifiers | The field's modifiers
[`Type`](#javadoc-type) fieldType | the [type](#javadoc-type) of the field.
[`Class`](#javadoc-class) class | the [class](#javadoc-class) of the field.

---
### Javadoc Parameter

Field | Description
--- | ---
`String` name | The parameter name
[`Type`](#javadoc-type) type | the [type](#javadoc-type) of the parameter
[`Array<Annotation>`](#javadoc-annotation) annotations | The method's [annotations](#javadoc-annotation)

---
### Javadoc Annotation

I've yet to see one of these...

---

---
## Endpoints
### Get Any
__URL__ `GET /javadoc/any/{path}`

>Gets the javadoc of any given path.

Output : one of [[`Class`](#javadoc-class),[`Array<Method>`](#javadoc-method),[`Field`](#javadoc-field)]

With extra property `type` which is one of [`class`,`methods`.`field`] respectively.

### Get Class
__URL__ `GET /javadoc/class/{classPath}`

>Gets the javadoc of any given class based on class path.

Output : [`Class`](#javadoc-class)

With extra property `type` which is `class`.
### Get Methods
__URL__ `GET /javadoc/methods/{methodPath}`

>Gets the javadoc of all methods with the given method path.

Output : [`Array<Method>`](#javadoc-method)

With extra property `type` which is `methods`.
### Get Field
__URL__ `GET /javadoc/field/{fieldPath}`

>Gets the javadoc of the field with the given field path.

Output : [`Field`](#javadoc-field)

With extra property `type` which is `field`.