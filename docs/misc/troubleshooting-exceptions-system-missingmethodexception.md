---
title: "Разрешение вопросов, связанных с исключениями: System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "MissingMethodException - класс"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.MissingMethodException
Исключение <xref:System.MissingMethodException> вызывается при попытке динамического доступа к несуществующему методу.  
  
## Полезные советы  
 **Если метод в библиотеке классов был удален или переименован, перекомпилируйте все сборки, ссылающиеся на этот метод.**  
 Это исключение обычно возникает при попытке динамического доступа к удаленному или переименованному методу сборки, к которому обращаются не по строгому имени.  
  
## Примечания  
 При вызове неуправляемой функции это исключение возникает, если среда CLR не может найти модуль или функцию.  
  
## См. также  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Устранение неполадок взаимодействия](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)