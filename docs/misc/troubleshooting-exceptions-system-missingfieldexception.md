---
title: "Разрешение вопросов, связанных с исключениями: System.MissingFieldException | Microsoft Docs"
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
  - "MissingFieldException - класс"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.MissingFieldException
Исключение <xref:System.MissingFieldException> возникающее при попытке динамического доступа к несуществующему полю.  
  
## Полезные советы  
 **Если поле в библиотеке классов было удалено или переименовано, перекомпилируйте все сборки, ссылающиеся на эту библиотеку.**  
 Это исключение возникает при попытке динамического доступа к перемещенному или удаленному полю сборки, к которому нет ссылки по его строгому имени.  
  
## См. также  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)