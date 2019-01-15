---
title: Управление цветом, стилем линий и другими свойствами фигур
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ea0b73470bc9f3bed76328c55d823cef3c5b8e9e
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269323"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Управление цветом, стилем линий и другими свойствами фигур

Некоторые свойства фигуры, такие как цвет «доступные». То есть свойства могут быть связаны со свойством домена фигуры. Другие специалисты прямое управление.

## <a name="exposing-a-property"></a>Предоставление доступа к свойству
 Некоторые свойства фигуры, такие как цвет может быть связан с значение свойства домена.

 В определении DSL выберите фигуры, соединителя или классом схемы. В меню щелкните правой кнопкой мыши, выберите **добавить предоставленный**, а затем выберите нужное свойство, такие как цвет заливки.

 Фигура теперь имеет свойство домена, которое можно задать в программном коде или имени пользователя.

## <a name="dynamically-updating-an-exposed-property"></a>Динамическое обновление открытого свойства
 Обычно требуется сделать зависимым от другого свойства открытого свойства. Например может потребоваться фигуру, чтобы включить красный всякий раз, когда определенного свойства домена меньше нуля. Чтобы сделать эту зависимость, создать [правило](../modeling/rules-propagate-changes-within-the-model.md). Пример:

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