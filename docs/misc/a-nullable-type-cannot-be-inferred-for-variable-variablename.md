---
title: "Тип, допускающий значения NULL, не может быть определен для переменной &quot;&lt;имя_переменной&gt;&quot; | Microsoft Docs"
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
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип, допускающий значения NULL, не может быть определен для переменной &quot;&lt;имя_переменной&gt;&quot;
Тип, допускающий значения NULL, нельзя определить на основе ссылочного типа, такого как массив, класс или `String`. Значение, на основе которого определяется тип данных, должно иметь тип значения. Приведенный ниже код иллюстрирует эту ошибку.  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **Идентификатор ошибки:** BC36628  
  
### Исправление ошибки  
  
-   Удалите назначение, допускающее значения NULL.  
  
## См. также  
 [Типы значения, допускающие Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)