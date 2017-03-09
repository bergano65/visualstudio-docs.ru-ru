---
title: "Разрешение вопросов, связанных с исключениями: System.IO.FileNotFoundException | Microsoft Docs"
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
  - "FileNotFoundException - класс"
  - "System.IO.FileNotFoundException - исключение"
ms.assetid: 6e5ab395-7c81-434e-835f-0fc792b9149d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.IO.FileNotFoundException
Исключение <xref:System.IO.FileNotFoundException> вызывается при попытке получить доступ к файлу или каталогу, не существующему на диске.  
  
## Полезные советы  
 **Убедитесь, что файл существует в указанном расположении.**  
 Если указанный файл не существует, вызывается это исключение. Для получения дополнительной информации см. <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>.  
  
 **При использовании относительных путей убедитесь, что текущий каталог правилен.**  
 Если текущий каталог неверен, относительные пути могут так же оказаться неверными.  
  
## См. также  
 <xref:System.IO.FileNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)