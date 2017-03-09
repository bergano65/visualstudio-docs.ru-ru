---
title: "Разрешение вопросов, связанных с исключениями: System.FieldAccessException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "FieldAccessException - класс"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.FieldAccessException
Исключение <xref:System.FieldAccessException> вызывается при недопустимой попытке доступа к личным или защищенным полям внутри класса.  
  
## Полезные советы  
 **Если уровень доступа к полю в библиотеке класса был изменен, необходимо перекомпилировать все сборки, ссылающиеся на эту библиотеку.**  
 Это исключение обычно вызывается при изменении уровня доступа \(`Public`, `Private`, и т.д.\) к полю в библиотеке класса и если не была перекомпилирована хотя бы одна сборка, ссылающаяся на библиотеку.  
  
## См. также  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)