---
title: DiscountAdjustment
description: API reference for DiscountAdjustment in Umbraco Commerce
---
## DiscountAdjustment

```csharp
public class DiscountAdjustment : PriceAdjustment<DiscountAdjustment>
```

**Inheritance**

* class [PriceAdjustment&lt;TSelf&gt;](priceadjustment-1.md)

**Namespace**
* [Umbraco.Commerce.Core.Models](README.md)

### Constructors

#### DiscountAdjustment

The default constructor.

```csharp
public DiscountAdjustment()
```


---

#### DiscountAdjustment (1 of 2)

```csharp
public DiscountAdjustment(DiscountReadOnly discount, Price price)
```

---

#### DiscountAdjustment (2 of 2)

```csharp
public DiscountAdjustment(Guid discountId, string discountName, Price price)
```


### Properties

#### DiscountId

```csharp
public Guid DiscountId { get; }
```


---

#### DiscountName

```csharp
public string DiscountName { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Umbraco.Commerce.Core.dll -->
