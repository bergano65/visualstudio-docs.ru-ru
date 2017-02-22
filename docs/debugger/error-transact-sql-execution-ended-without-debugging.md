---
title: "Ошибка: выполнение Transact-SQL завершается без отладки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_sql_executed_but_not_debugged"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: выполнение Transact-SQL завершается без отладки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта ошибка возникает при попытке отладки Transact\-SQL или процедуры SQLCLR, если отладчик не получает сообщения об отладке от SQL Server.  
  
 Это может быть вызвано проблемами сети или проблемами на сервере SQL Server, однако наиболее вероятная причина — проблемы с правами доступа.  
  
 Принимают участие две учетные записи:  
  
-   Учетная запись приложения является учетной записью пользователя, с которой выполняется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Учетная запись соединения — это идентификация, используемая для подключения к SQL Server.  Эти учетные данные не обязательно совпадают с учетными данными, с которыми выполняется Visual Studio, таким образом, как если бы при соединении использовалась проверка подлинности SQL.  
  
 Для отладки SQL необходимо, чтобы учетная запись приложения соответствовала учетной записи соединения или была учетной записью администратора.  
  
 При использовании имени входа в систему SQL, такого как "sa", учетная запись приложения должна быть установлена на SQL Server как учетная запись администратора.  По умолчанию администраторы компьютера, на котором выполняется сервер SQL, являются администраторами SQL Server.  
  
 Чтобы устранить эту ошибку, необходимо:  
  
-   Проверить установленные параметры прав доступа.  Дополнительные сведения см. в разделе [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/ru-ru/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Удостовериться в том, что отладка SQL настроена верно.  
  
-   Обратиться за консультацией к администратору сети или администратору базы данных.  
  
## См. также  
 [Setting Up SQL Debugging](http://msdn.microsoft.com/ru-ru/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/ru-ru/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Параметры отладки и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)