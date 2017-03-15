---
title: "Элемент &quot;&lt;имя_элемента&gt;&quot; является устаревшим (ошибка Visual Basic) | Microsoft Docs"
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
  - "vbc31075"
  - "bc31075"
helpviewer_keywords: 
  - "BC31075"
ms.assetid: 614d36a1-2fba-4d03-963c-1565e88b08a6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Элемент &quot;&lt;имя_элемента&gt;&quot; является устаревшим (ошибка Visual Basic)
Оператор пытается получить доступ к программному элементу, который был помечен атрибутом <xref:System.ObsoleteAttribute> и директивой, предписывающей расценивать это как ошибку.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute>. Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 **Идентификатор ошибки:** BC31075  
  
### Исправление ошибки  
  
-   Убедитесь, что в ссылке исходного кода имя элемента указано правильно.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)