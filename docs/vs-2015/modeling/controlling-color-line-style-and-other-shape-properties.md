---
title: Управление цветом, стилем линий и другими свойствами фигур | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667858"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Управление цветом, стилем линий и другими свойствами фигур
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Некоторые свойства формы, например Color, могут быть "представляемыми", т. е. связанными со свойством предметной области фигуры. Другие должны управляться напрямую.

## <a name="exposing-a-property"></a>Предоставление доступа к свойству
 Некоторые свойства формы, такие как Color, могут быть связаны со значением свойства предметной области.

 В определении DSL выберите класс фигуры, соединителя или схемы. В контекстном меню выберите **добавить предоставленный**, а затем выберите нужное свойство, например цвет заливки.

 Теперь фигура имеет свойство предметной области, которое можно задать в программном коде или в качестве пользователя.

## <a name="dynamically-updating-an-exposed-property"></a>Динамическое обновление доступного свойства
 Обычно необходимо сделать предоставляемое свойство зависимым от другого свойства. Например, фигуру может быть назначен красный цвет, если определенное свойство домена меньше нуля. Чтобы сделать эту зависимость, создайте [правило](../modeling/rules-propagate-changes-within-the-model.md). Пример:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```
