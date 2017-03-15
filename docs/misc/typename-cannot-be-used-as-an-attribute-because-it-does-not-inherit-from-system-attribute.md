---
title: "&quot;&lt;имя_типа&gt;&quot; не может использоваться как атрибут, так как не является производным от System.Attribute | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_типа&gt;&quot; не может использоваться как атрибут, так как не является производным от System.Attribute
Была предпринята попытка использовать класс, который не является производным от `System.Attribute`.  
  
 **Идентификатор ошибки:** BC31504  
  
### Исправление ошибки  
  
1.  Определите пользовательские атрибуты как классы, производные от `System.Attribute`, добавив оператор `Imports` в первую строку кода класса.  
  
## См. также  
 <xref:System.AttributeUsageAttribute>   
 [НЕ В СБОРКЕ. Настраиваемые атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/d72d8a5c-8f64-4614-b15b-cad66845d047)