---
title: "Атрибут System.Runtime.InteropServices.DispIdAttribute не может применяться к &quot;&lt;имя_типа&gt;&quot;, поскольку атрибут Microsoft.VisualBasic.ComClassAttribute резервирует отрицательные значения | Microsoft Docs"
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
  - "bc32506"
  - "vbc32506"
helpviewer_keywords: 
  - "BC32506"
ms.assetid: c6f52e1d-45d8-45cb-9ecb-a2f23b3ca779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут System.Runtime.InteropServices.DispIdAttribute не может применяться к &quot;&lt;имя_типа&gt;&quot;, поскольку атрибут Microsoft.VisualBasic.ComClassAttribute резервирует отрицательные значения
Блок атрибутов <xref:System.Runtime.InteropServices.DispIdAttribute> указывает отрицательное значение DISPID, которое зарезервировано атрибутом `COMClassAttribute` для специальных функций в классе, к которому он применяется.  
  
 Идентификатор диспетчеризации \(DISPID\) используется в COM в качестве аргумента метода `IDispatch:Invoke` для доступа к свойствам и методам, предоставляемым COM\-объектом.  
  
 **Идентификатор ошибки:** BC32506  
  
### Исправление ошибки  
  
-   Укажите значение DISPID больше нуля в атрибуте `DispIdAttribute`.  
  
## См. также  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Класс ComClassAttribute](http://msdn.microsoft.com/ru-ru/5c2f0835-9210-47dc-bc59-5c1769953574)