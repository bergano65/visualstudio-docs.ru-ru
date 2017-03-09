---
title: "Разрешение вопросов, связанных с исключениями: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SqlCeInvalidDatabaseFormatException - исключение"
  - "System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException - исключение"
ms.assetid: f5ca1f40-4619-4523-807e-d5b20bfb05b0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Разрешение вопросов, связанных с исключениями: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException
Исключение `System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException` возникает, когда SQL Server Compact открывает файл базы данных, созданный с помощью более ранней версии продукта.  
  
## Примечания  
 Можно обновить файл базы данных с помощью [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] или используя API `System.Data.SqlServerCe.SqlCeEngine.Upgrade`.  
  
 Для получения дополнительной информации см. [Библиотека классов SQL Server Compact 3.5](http://go.microsoft.com/fwlink/?LinkID=102595).  
  
## См. также  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)