---
title: "Ошибка. Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка. Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Хранимую процедуру sp\_enable\_sql\_debug не удалось выполнить на сервере.  Для этого могут быть следующие причины:  
  
-   Проблема подключения.  Подключение к серверу должно быть стабильным.  
  
-   Отсутствие необходимых разрешений на сервере.  Для отладки на SQL Server 2005 учетная запись, запущенная Visual Studio, и учетная запись, используемая для подключения к SQL Server, должны быть членами роли системного администратора.  Учетная запись, используемая для подключения к SQL Server, является либо учетной записью Windows \(при использовании проверки подлинности Windows\) либо учетной записью с идентификатором пользователя и паролем \(при использовании проверки подлинности SQL\).  
  
 Дополнительные сведения см. в разделе [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/ru-ru/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## См. также  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/ru-ru/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/ru-ru/3db09e68-edcc-42de-9c22-4e97cfd55ab3)