---
title: "Метод доступа &quot;&lt;ключевое_слово&gt;&quot; свойства &quot;&lt;имя_свойства&gt;&quot; устарел (ошибка Visual Basic) | Microsoft Docs"
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
  - "vbc30912"
  - "bc30912"
helpviewer_keywords: 
  - "BC30912"
ms.assetid: f1fa965e-090c-49f3-ab1e-cbb2f9b2a5f0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Метод доступа &quot;&lt;ключевое_слово&gt;&quot; свойства &quot;&lt;имя_свойства&gt;&quot; устарел (ошибка Visual Basic)
Оператор пытается прочитать или записать свойство, для которого соответствующая процедура была помечена атрибутом <xref:System.ObsoleteAttribute>; в этой ситуации компилятор выдает ошибку.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему атрибут <xref:System.ObsoleteAttribute>. Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 **Идентификатор ошибки:** BC30912  
  
### Исправление ошибки  
  
1.  Убедитесь, что имя свойства в исходном коде написано правильно.  
  
2.  Избегайте доступа к свойству способом \(чтение или запись\), который приводит к возникновению этого сообщения.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Процедуры свойств](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)