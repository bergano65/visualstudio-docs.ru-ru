---
title: "Свойству &quot;&lt;поле_свойства&gt;&quot; с атрибутом Shared не может присваиваться значение | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31500"
  - "vbc31500"
helpviewer_keywords: 
  - "BC31500"
ms.assetid: dffa2b07-9609-4aa3-ae58-c0804d8a05d6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Свойству &quot;&lt;поле_свойства&gt;&quot; с атрибутом Shared не может присваиваться значение
Предпринята попытка присвоить значение свойству `ReadOnly` или `Shared` в атрибуте.  
  
 **Идентификатор ошибки:** BC31500  
  
### Исправление ошибки  
  
1.  Удалите оператор присваивания значения свойству.  
  
2.  Если используемое свойство было создано вами, удалите из свойства атрибута модификатор `ReadOnly` или `Shared`.  
  
## См. также  
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)