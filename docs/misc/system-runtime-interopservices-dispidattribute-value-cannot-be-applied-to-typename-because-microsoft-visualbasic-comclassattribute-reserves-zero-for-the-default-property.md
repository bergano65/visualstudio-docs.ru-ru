---
title: "Не удается применить значение System.Runtime.InteropServices.DispIdAttribute к типу &quot;&lt;имя_типа&gt;&quot;, поскольку для аргумента Microsoft.VisualBasic.ComClassAttribute в качестве свойства, используемого по умолчанию, зарезервирован ноль | Microsoft Docs"
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
  - "vbc32505"
  - "bc32505"
helpviewer_keywords: 
  - "BC32505"
ms.assetid: a7d5b948-2d72-48b1-8baf-bfaae36b0128
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается применить значение System.Runtime.InteropServices.DispIdAttribute к типу &quot;&lt;имя_типа&gt;&quot;, поскольку для аргумента Microsoft.VisualBasic.ComClassAttribute в качестве свойства, используемого по умолчанию, зарезервирован ноль
В блоке атрибута <xref:System.Runtime.InteropServices.DispIdAttribute> для DISPID установлено нулевое значение, которое резервируется `COMClassAttribute` для представления свойства по умолчанию соответствующего класса.  
  
 Идентификатор диспетчеризации \(DISPID\) используется в COM в качестве аргумента метода `IDispatch:Invoke` для доступа к свойствам и методам, предоставляемым COM\-объектом.  
  
 **Идентификатор ошибки:** BC32505  
  
### Исправление ошибки  
  
-   Укажите значение DISPID больше нуля в атрибуте <xref:System.Runtime.InteropServices.DispIdAttribute>.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Класс ComClassAttribute](http://msdn.microsoft.com/ru-ru/5c2f0835-9210-47dc-bc59-5c1769953574)