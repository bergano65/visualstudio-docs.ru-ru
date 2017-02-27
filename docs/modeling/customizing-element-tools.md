---
title: "Настройка средств элемента | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 6
---
# Настройка средств элемента
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В некоторые определения DSL представляют один понятие как группу элементов. Например при создании модели, в котором компонент имеет фиксированный набор портов, всегда требуется порты, создаваемых одновременно их родительского компонента. Таким образом необходимо настроить средство создания элемента, он создает группу элементов, вместо одного. Чтобы добиться этого, можно настроить способ инициализации средство создания элемента.  
  
 Также можно переопределить, что происходит при перетаскивании на схему или на элемент средство.  
  
## Настройка средства элемента содержимого  
 Каждое средство элемента хранит экземпляр <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\), который содержит сериализованная версия одного или нескольких элементов модели и ссылки. По умолчанию EGP средства элемента содержит один экземпляр класса, укажите для инструмента. Это можно изменить, переопределив *ваш язык*`ToolboxHelper.CreateElementToolPrototype`. Этот метод вызывается, когда загружается пакет доменного языка.  
  
 Параметр метода — идентификатор класса, указанного в определении DSL. При вызове метода с классом, который вас интересует, можно добавить дополнительные элементы в EGP.  
  
 EGP должен включать внедрение связей от одного основного элемента для дочерних элементов. Он также может включать ссылки.  
  
 В следующем примере создается основной элемент и два встроенных элементов. Основной класс называется Придерживающихся, и он имеет два отношения внедрения для элементов с именем терминалов. Внедрение свойства роли с именами Terminal1 и Terminal2, и оба имеют кратность 1.. 1.  
  
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
  
## См. также  
 [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)