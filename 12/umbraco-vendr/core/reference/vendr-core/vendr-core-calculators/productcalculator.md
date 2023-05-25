---
title: ProductCalculator
description: API reference for ProductCalculator in Vendr, the eCommerce solution for Umbraco
---
## ProductCalculator

```csharp
public class ProductCalculator : ProductCalculatorBase
```

**Inheritance**

* class [ProductCalculatorBase](../productcalculatorbase/)

**Namespace**
* [Vendr.Core.Calculators](../)

### Constructors

#### ProductCalculator

```csharp
public ProductCalculator(ITaxService taxService, IStoreService storeService)
```


### Methods

#### CalculateProductPrice

```csharp
public override Price CalculateProductPrice(IProductSnapshot productSnapshot, Guid currencyId, 
    TaxRate taxRate, ProductCalculatorContext context)
```


---

#### CalculateProductTaxRate

```csharp
public override TaxRate CalculateProductTaxRate(IProductSnapshot productSnapshot, 
    TaxSource taxSource, TaxRate fallbackTaxRate, ProductCalculatorContext context)
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->