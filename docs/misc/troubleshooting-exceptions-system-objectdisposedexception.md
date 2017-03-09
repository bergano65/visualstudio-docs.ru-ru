---
title: "Разрешение вопросов, связанных с исключениями: System.ObjectDisposedException | Microsoft Docs"
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
  - "класс ObjectDisposedException, устранение неполадок"
ms.assetid: 702912b6-e927-4f8e-8b7c-2e1880312b0e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.ObjectDisposedException
Исключение <xref:System.ObjectDisposedException> возникает при попытке выполнить операцию на уничтоженном объекте — например закрытом потоке или разделе реестра.  
  
## Полезные советы  
 **Проверьте, не освободили ли вы ресурс перед попыткой его использования.**  
 Например, при попытке управлять потоком убедитесь, что он еще не закрыт.  
  
## См. также  
 <xref:System.ObjectDisposedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)