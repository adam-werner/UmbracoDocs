---
title: RegionNotificationEventBase<TEntity>
description: API reference for RegionNotificationEventBase<TEntity> in Umbraco Commerce
---
## RegionNotificationEventBase&lt;TEntity&gt;

```csharp
public abstract class RegionNotificationEventBase<TEntity> : NotificationEventBase
    where TEntity : RegionReadOnly
```

**Inheritance**

* class [NotificationEventBase](../../umbraco-commerce-common/umbraco-commerce-common-events/notificationeventbase.md)

**Namespace**
* [Umbraco.Commerce.Core.Events.Notification](README.md)

### Constructors

#### RegionNotificationEventBase&lt;TEntity&gt;

```csharp
public RegionNotificationEventBase(TEntity region)
```


### Properties

#### Region

```csharp
public TEntity Region { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Umbraco.Commerce.Core.dll -->
