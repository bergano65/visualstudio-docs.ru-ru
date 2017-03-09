---
title: "&quot;System.Nullable&quot; не удовлетворяет ограничению &quot;Structure&quot; для параметра типа &quot;&lt;имя_параметра_типа&gt;&quot; | Microsoft Docs"
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
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;System.Nullable&quot; не удовлетворяет ограничению &quot;Structure&quot; для параметра типа &quot;&lt;имя_параметра_типа&gt;&quot;
Универсальный тип, представляемый аргументом типа <xref:System.Nullable%601>, передается в параметр типа, который имеет ограничение `Structure`.  
  
 Среда CLR специально запрещает использовать структуру <xref:System.Nullable%601> в качестве аргумента типа для самой себя. Даже если структура и удовлетворяла бы ограничению `Structure`, ее рекурсивное использование могло бы привести к неуклюжим конструкциям, например `Nullable(Of Nullable(Of Nullable))`.  
  
 **Идентификатор ошибки:** BC32115  
  
### Исправление ошибки  
  
-   Удалите ограничение `Structure` из параметра типа или измените аргумент типа на тип значения, отличный от <xref:System.Nullable%601>.  
  
## См. также  
 <xref:System.Nullable%601>   
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Структура \(Visual Basic\)](http://msdn.microsoft.com/ru-ru/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)