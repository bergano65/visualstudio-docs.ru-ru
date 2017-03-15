---
title: "Не удается преобразовать тип &quot;тип1&quot; в &quot;тип2&quot; | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Не удается преобразовать тип &quot;тип1&quot; в &quot;тип2&quot;
Не удается преобразовать тип "тип1" в "тип2". Вы можете использовать свойство Value, чтобы получить строковое значение первого элемента объекта "родительскийЭлемент".  
  
 Предпринята попытка неявного приведения XML\-литерала к определенному типу. XML\-литерал не может быть неявно приведен к указанному типу.  
  
 **Идентификатор ошибки:** BC31193  
  
### Исправление ошибки  
  
-   Используйте свойство `Value` XML\-литерала для ссылки на его значение как на `String`. Используйте функцию `CType`, другую функцию преобразования типа или класс <xref:System.Convert> для приведения значения к указанному типу.  
  
## См. также  
 <xref:System.Convert>   
 [Доступ к XML в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/xml/accessing-xml)   
 [Функции преобразования типов](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [XML\-литералы](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)