---
title: Управление цветом, стиль линии и другими свойствами фигур | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1722a3f8a5ff05589cfad987fff6448d44e96ec8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558150"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Управление цветом, стилем линий и другими свойствами фигур
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [управление цвет, стиль линии и другими свойствами фигур](https://docs.microsoft.com/visualstudio/modeling/controlling-color-line-style-and-other-shape-properties).  
  
Некоторые свойства фигуры такие как цвет «доступные» — то есть связанного свойства домена фигуры. Другие специалисты прямое управление.  
  
## <a name="exposing-a-property"></a>Предоставление доступа к свойству  
 Некоторые свойства фигуры, такие как цвет может быть связан с значение свойства домена.  
  
 В определении DSL выберите фигуры, соединителя или классом схемы. В контекстном меню, выберите **добавить предоставленный**, а затем выберите нужное свойство, такие как цвет заливки.  
  
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



