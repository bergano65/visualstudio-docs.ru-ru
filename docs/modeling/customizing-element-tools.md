---
title: Настройка средств элемента
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ee9f574b1d0db7a90b2d056456ccb29db0604e1e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846104"
---
# <a name="customizing-element-tools"></a>Настройка средств элемента
В некоторых определениях DSL единую концепцию представляют группу элементов. Например при создании модели, в котором компонент имеет фиксированный набор портов, всегда требуется порты, которые нужно создать в то же время, как их родительского компонента. Таким образом необходимо настроить средство создания элемента, таким образом, чтобы он создает группу элементов, вместо одного. Для этого можно настроить способ инициализации средства создания элемента.

 Также можно переопределить, что происходит, когда средство перетаскивается на диаграмму или элемент.

## <a name="customizing-the-content-of-an-element-tool"></a>Настройка содержимого средства элемента
 Каждое средство элемента хранит экземпляр <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), который содержит сериализованную версию одного или нескольких элементов модели, так и ссылки. По умолчанию EGP средства элемента содержит один экземпляр класса, укажите для инструмента. Это можно изменить, переопределив *ваш язык*`ToolboxHelper.CreateElementToolPrototype`. Этот метод вызывается, когда загружается пакет доменного языка.

 Параметр метода является идентификатор класса, который указан в определении DSL. При вызове метода в классе, которые вас интересуют, можно добавить дополнительные элементы в EGP.

 EGP должен включать внедрение связей от одного основного элемента для дочерних элементов. Оно также может включать ссылки на.

 В следующем примере создается главный элемент и два встроенных элементов. Основной класс называется резистор, и он имеет два отношения внедрения для элементов с именем терминалов. Внедрение свойства роли с именами Terminal1 и Terminal2, и оба имеют кратность 1..1.

```csharp
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>См. также

- [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)