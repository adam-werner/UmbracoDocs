---
title: FrozenPrice
description: API reference for FrozenPrice in Umbraco Commerce
---
## FrozenPrice

```csharp
public class FrozenPrice : EntityBase
```

**Inheritance**

* class [EntityBase](entitybase.md)

**Namespace**
* [Umbraco.Commerce.Core.Models](README.md)

### Constructors

#### FrozenPrice (1 of 2)

```csharp
public FrozenPrice(Guid orderId, string key, FreezablePrice price)
```

---

#### FrozenPrice (2 of 2)

```csharp
public FrozenPrice(Guid id, Guid orderId, string key, FreezablePrice price, DateTime created)
```


### Properties

#### CreateDate

```csharp
public DateTime CreateDate { get; set; }
```


---

#### Id

```csharp
public override Guid Id { get; }
```


---

#### Key

```csharp
public string Key { get; }
```


---

#### OrderId

```csharp
public Guid OrderId { get; }
```


---

#### Price

```csharp
public FreezablePrice Price { get; set; }
```


### Methods

#### DeepClone

```csharp
public override object DeepClone()
```


<!-- DO NOT EDIT: generated by xmldocmd for Umbraco.Commerce.Core.dll -->
