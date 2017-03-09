---
title: "Разрешение вопросов, связанных с исключениями: System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeploymentDownloadException - класс"
  - "развертывание приложений [C#], класс DeploymentDownloadException"
  - "развертывание приложений [C#], класс DeploymentDownloadException"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.DeploymentFramework.DeploymentDownloadException
Исключение `T:System.DeploymentFramework.DeploymentDownloadException` вызывается при возникновении сетевого исключения во время загрузки обновления приложения.  
  
## Полезные советы  
 **Просмотрите InnerException, чтобы определить базовое исключение System.Net или System.IO.**  
 Это исключение возникает всякий раз, когда возникает сетевое исключение при загрузке обновления приложения. Проверьте свойство <xref:System.Exception.InnerException%2A> исключения для определения базового исключения.  
  
## См. также  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Оператор Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)