---
title: ValidatePrintTemplateNameChange
description: API reference for ValidatePrintTemplateNameChange in Umbraco Commerce
---
## ValidatePrintTemplateNameChange

```csharp
public class ValidatePrintTemplateNameChange : ValidationEventBase
```

**Inheritance**

* class [ValidationEventBase](../../umbraco-commerce-common/umbraco-commerce-common-events/validationeventbase.md)

**Namespace**
* [Umbraco.Commerce.Core.Events.Validation](README.md)

### Constructors

#### ValidatePrintTemplateNameChange

```csharp
public ValidatePrintTemplateNameChange(PrintTemplateReadOnly printTemplate, 
    ChangingValue<string> name)
```


### Properties

#### Name

```csharp
public ChangingValue<string> Name { get; }
```


---

#### PrintTemplate

```csharp
public PrintTemplateReadOnly PrintTemplate { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Umbraco.Commerce.Core.dll -->
