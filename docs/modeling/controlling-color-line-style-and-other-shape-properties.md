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
ms.technology: vs-ide-modeling
ms.openlocfilehash: bfe0cbdda1b3eaa7d1afc936c7dbba75df6da07b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Управление цветом, стилем линий и другими свойствами фигур
Некоторые свойства фигуры такие как цвет «доступные» - т. е связать свойства домена фигуры. Другим пользователям требуется прямое управление.

## <a name="exposing-a-property"></a>Предоставление доступа к свойству
 Значение свойства домена могут быть связаны некоторые свойства фигуры, например цвет.

 В определении DSL выберите фигуры, соединителя или класс схемы. В контекстном меню, выберите **добавьте предоставляется**и выберите нужное свойство, такие как цвет заливки.

 Фигура теперь имеет свойства домена, который можно задать в коде программы или имени пользователя.

## <a name="dynamically-updating-an-exposed-property"></a>Динамическое обновление открытого свойства.
 Обычно необходимо сделать зависимым от другого свойства открытого свойства. Например может потребоваться фигуру, чтобы красным цветом всякий раз, когда свойство определенного домена меньше нуля. Чтобы добавить эту зависимость, создайте [правило](../modeling/rules-propagate-changes-within-the-model.md). Пример:

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