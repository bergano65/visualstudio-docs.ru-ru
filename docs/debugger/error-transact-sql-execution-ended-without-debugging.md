---
title: 'Ошибка: Выполнение Transact-SQL завершено без отладки | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 793e516c334d39cd7befc82a15e793df44d22f3b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Ошибка: выполнение Transact-SQL завершается без отладки
Эта ошибка возникает при попытке отладки Transact-SQL или процедуры SQLCLR, если отладчик не получает сообщения об отладке от SQL Server.  
  
 Это может быть вызвано проблемами сети или проблемами на сервере SQL Server, однако наиболее вероятная причина — проблемы с правами доступа.  
  
 Принимают участие две учетные записи:  
  
-   Учетная запись приложения является учетной записью пользователя, с которой выполняется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Учетная запись соединения — это идентификация, используемая для подключения к SQL Server. Эти учетные данные не обязательно совпадают с учетными данными, с которыми выполняется Visual Studio, таким образом, как если бы при соединении использовалась проверка подлинности SQL.  
  
 Для отладки SQL необходимо, чтобы учетная запись приложения соответствовала учетной записи соединения или была учетной записью администратора.  
  
 При использовании имени входа в систему SQL, такого как "sa", учетная запись приложения должна быть установлена на SQL Server как учетная запись администратора. По умолчанию администраторы компьютера, на котором выполняется сервер SQL, являются администраторами SQL Server.  
  
 Чтобы устранить эту ошибку, необходимо:  
  
-   Проверить установленные параметры прав доступа. Дополнительные сведения см. в разделе [как: Настройка разрешений SQL Server для отладки](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Удостовериться в том, что отладка SQL настроена верно.  
  
-   Обратиться за консультацией к администратору сети или администратору базы данных.  
  
## <a name="see-also"></a>См. также  
 [Настройка отладки SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Как: задать разрешения SQL Server для отладки](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)