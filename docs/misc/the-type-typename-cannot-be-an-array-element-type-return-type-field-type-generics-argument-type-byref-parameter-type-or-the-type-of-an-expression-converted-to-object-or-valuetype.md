---
title: "Тип &quot;&lt;имя_типа&gt;&quot; не может быть типом элемента массива, типом возврата, типом поля, универсальным типом аргумента, типом параметра ByRef или типом выражения, преобразованным в Object или ValueType. | Microsoft Docs"
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
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Тип &quot;&lt;имя_типа&gt;&quot; не может быть типом элемента массива, типом возврата, типом поля, универсальным типом аргумента, типом параметра ByRef или типом выражения, преобразованным в Object или ValueType.
Выражение объявляет переменную, параметр процедуры, параметр типа, возвращаемое функцией значение или массив как ограниченный тип.  
  
 Среда CLR предоставляет определенные типы исключительно для специальной языковой поддержки, и они не должны использоваться как типы данных в приложении. Эти типы включают структуры <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle> и <xref:System.TypedReference>.  
  
 **Идентификатор ошибки:** BC31396  
  
### Исправление ошибки  
  
-   Не используйте ограниченную структуру в качестве объявленного типа данных.  
  
## См. также  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>