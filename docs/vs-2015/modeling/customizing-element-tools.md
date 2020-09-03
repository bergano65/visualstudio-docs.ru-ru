---
title: Настройка инструментов элементов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655013"
---
# <a name="customizing-element-tools"></a>Настройка средств элемента
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В некоторых определениях DSL одна концепция представляется как группа элементов. Например, при создании модели, в которой компонент имеет фиксированный набор портов, вы всегда хотите, чтобы порты создавались одновременно с родительским компонентом. Поэтому необходимо настроить средство создания элементов таким образом, чтобы оно создавало группу элементов, а не только один. Чтобы добиться этого, можно настроить инициализацию инструмента создания элементов.

 Можно также переопределить то, что происходит при перетаскивании инструмента на схему или элемент.

## <a name="customizing-the-content-of-an-element-tool"></a>Настройка содержимого инструмента элемента
 Каждый инструмент элемента хранит экземпляр <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (ЕГП), который содержит сериализованную версию одного или нескольких элементов модели и ссылок. По умолчанию ЕГП инструмента element содержит один экземпляр класса, указанный для средства. Это можно изменить путем переопределения *вашязык* `ToolboxHelper.CreateElementToolPrototype` . Этот метод вызывается при загрузке пакета DSL.

 Параметр метода является ИДЕНТИФИКАТОРом класса, указанного в определении DSL. Когда метод вызывается с интересующим вас классом, в ЕГП можно добавить дополнительные элементы.

 ЕГП должен включать ссылки внедрения из одного главного элемента в дочерние элементы. Он также может включать ссылки на справочные материалы.

 В следующем примере создается элемент Main и два внедренных элемента. Основной класс называется резистором и имеет две связи внедрения с элементами с именем Terminal. Свойства роли внедрения называются Terminal1 и Terminal2, а обе имеют кратность 1.. 1.

```
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

## <a name="see-also"></a>См. также:
 [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)
