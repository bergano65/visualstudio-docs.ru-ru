---
title: "Член &quot;&lt;имя_члена&gt;&quot; устарел: &quot;&lt;сообщение_об_ошибке&gt;&quot; | Microsoft Docs"
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
  - "bc30668"
  - "vbc30668"
helpviewer_keywords: 
  - "BC30668"
ms.assetid: 25e5606c-2734-4f42-a2bc-1ad28ec1e892
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Член &quot;&lt;имя_члена&gt;&quot; устарел: &quot;&lt;сообщение_об_ошибке&gt;&quot;
Оператор пытается получить доступ к члену класса или структуры, который был помечен атрибутом <xref:System.ObsoleteAttribute>, и директивой, предписывающие расценивать это как ошибку.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute>. Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 **Идентификатор ошибки**: BC30668  
  
### Исправление ошибки  
  
1.  Проверьте указанное сообщение об ошибке и предпримите соответствующее действие.  
  
2.  Убедитесь в том, что в ссылке исходного кода имя члена указано правильно.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)