---
title: 'Ошибка: Пользователь может не выполнить хранимую процедуру sp_enable_sql_debug | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc18953a8312d9ff1f4eef700fe0508b13409c67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Ошибка. Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug
Хранимую процедуру sp_enable_sql_debug не удалось выполнить на сервере. Для этого могут быть следующие причины:  
  
-   Проблема подключения. Подключение к серверу должно быть стабильным.  
  
-   Отсутствие необходимых разрешений на сервере. Для отладки на SQL Server 2005 учетная запись, запущенная Visual Studio, и учетная запись, используемая для подключения к SQL Server, должны быть членами роли системного администратора. Учетная запись, используемая для подключения к SQL Server, является либо учетной записью Windows (при использовании проверки подлинности Windows) либо учетной записью с идентификатором пользователя и паролем (при использовании проверки подлинности SQL).  
  
 Дополнительные сведения см. в разделе [как: Настройка разрешений SQL Server для отладки](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>См. также  
 [Как: задать разрешения SQL Server для отладки](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Настройка отладки SQL](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)