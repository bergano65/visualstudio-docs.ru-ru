---
title: "Разрешение вопросов, связанных с исключениями: Microsoft.Office.Tools.CannotRemoveControlException | Microsoft Docs"
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
  - "Microsoft.Office.Tools.CannotRemoveControlException - исключение"
ms.assetid: 0c806cb7-b34b-4664-999b-4621efd97414
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: Microsoft.Office.Tools.CannotRemoveControlException
Исключение <xref:Microsoft.Office.Tools.CannotRemoveControlException> возникает при попытке программно удалить элемент управления, который был добавлен не программно.  
  
## Полезные советы  
 Можно программно удалить элемент управления только если он был добавлен программными средствами.  
 -   Можно программно удалить элемент управления только если он был добавлен программными средствами. Если элемент управления был добавлен в документ в режиме разработки, а не во время выполнения, он не может быть удален.  
  
## См. также  
 <xref:Microsoft.Office.Tools.CannotRemoveControlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)