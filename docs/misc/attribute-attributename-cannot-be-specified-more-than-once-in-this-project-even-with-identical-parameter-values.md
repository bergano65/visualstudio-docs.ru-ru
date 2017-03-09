---
title: "В этом проекте атрибут &quot;&lt;имя_атрибута&gt;&quot; не может быть задан повторно даже с теми же значениями параметров | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В этом проекте атрибут &quot;&lt;имя_атрибута&gt;&quot; не может быть задан повторно даже с теми же значениями параметров
Настраиваемый атрибут указан более одного раза в том же элементе программирования, но к этому атрибуту применен <xref:System.AttributeUsageAttribute>, а его свойство <xref:System.AttributeUsageAttribute.AllowMultiple%2A> установленное в значение `False`.<xref:System.AttributeUsageAttribute.AllowMultiple%2A> определяет, можно ли использовать атрибут несколько раз.  
  
 По умолчанию данное сообщение является предупреждением. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC41000  
  
### Исправление ошибки  
  
-   Удалите лишнюю спецификацию настраиваемого атрибута или установите <xref:System.AttributeUsageAttribute.AllowMultiple%2A> в значение `True` в примененном к нему атрибуте <xref:System.AttributeUsageAttribute>.  
  
## См. также  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)