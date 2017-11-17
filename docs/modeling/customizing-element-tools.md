---
title: "Настройка средств элемент | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2555fe2be42ed58482cdacf174a6cb035a8d7bd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-element-tools"></a>Настройка средств элемента
В некоторые определения DSL представляют один понятие как группу элементов. Например при создании модели, в котором компонент имеет фиксированный набор портов, всегда требуется порты, создаваемых одновременно их родительского компонента. Таким образом необходимо настроить средство создания элемента, он создает группу элементов, а несколько. Чтобы добиться этого, можно настроить способ инициализации средство создания элемента.  
  
 Также можно переопределить, что происходит при перетаскивании на схему или элемент средство.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Настройка содержимого средством для элементов  
 Каждое средство элемент сохраняет экземпляр <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), который содержит сериализованная версия одного или нескольких элементов модели и ссылок. По умолчанию EGP средством для элементов содержит один экземпляр класса, который можно указать для средства. Это можно изменить, переопределив *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Этот метод вызывается, когда загружается пакет DSL.  
  
 Параметр метода является Идентификатором класса, который указан в определении DSL. При вызове метода в классе, которые вас интересуют, вы можете добавить дополнительные элементы в EGP.  
  
 EGP должен включать внедрение ссылки из одного основного элемента на их дочерние элементы. Он также может включать ссылки для справки.  
  
 В следующем примере создается элемент main и два встроенных элементов. Основной класс называется резистор, и он имеет две связи внедренные элементы с именем терминалов. Внедрение свойства роли с именами Terminal1 и Terminal2, и оба имеют кратность 1..1.  
  
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
  
## <a name="see-also"></a>См. также  
 [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)