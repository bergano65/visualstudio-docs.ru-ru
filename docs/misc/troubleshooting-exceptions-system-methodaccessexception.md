---
title: "Разрешение вопросов, связанных с исключениями: System.MethodAccessException | Microsoft Docs"
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
  - "MethodAccessException - класс"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.MethodAccessException
Исключение <xref:System.MethodAccessException> возникает при недопустимой попытке доступа к private или protected методам внутри класса.  
  
## Полезные советы  
 **Если уровень доступа для метода в библиотеке классов был изменен, перекомпилируйте все сборки, которые ссылаются на эту библиотеку.**  
 Это исключение обычно возникает, когда вызывающий метод не имеет разрешения на доступ к элементу.  
  
## См. также  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)