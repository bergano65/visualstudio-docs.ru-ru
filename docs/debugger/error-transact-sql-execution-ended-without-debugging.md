---
title: 'Ошибка: Выполнение Transact-SQL завершено без отладки | Документация Майкрософт'
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17c1854826de2314dfe8124d99f6ec6c8899ee70
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011225"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Ошибка: Выполнение Transact-SQL завершается без отладки

Эта ошибка возникает при попытке отладки Transact-SQL или процедуры SQLCLR и отладчик не получает сообщения об отладке от SQL Server.  
  
Эта проблема может быть следствием сетевых проблем или проблем на сервере SQL Server, но наиболее вероятной причиной является проблема с разрешениями.  
  
Принимают участие две учетные записи:  
  
- Учетная запись приложения является учетной записью пользователя, с которой выполняется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Учетная запись соединения — это идентификация, используемая для подключения к SQL Server. Эта учетная запись не обязательно совпадают с учетными данными, на котором выполняется Visual Studio, как, если соединение использует проверку подлинности SQL.  
  
  Отладка SQL требует учетной записи приложения должен соответствовать учетной записи подключения или входить в роль sysadmin.  
  
  Если вы используете имя учетной записи SQL, например sa, учетной записи приложений должны настраиваться в SQL Server как учетная запись администратора. По умолчанию Администраторы на компьютере под управлением SQL server, являются администраторами SQL Server.  
  
  Чтобы устранить эту ошибку, необходимо:  
  
  - Проверить установленные параметры прав доступа. Дополнительные сведения см. в разделе [Как Задайте разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
  - Удостовериться в том, что отладка SQL настроена верно.  
  
  - Обратиться за консультацией к администратору сети или администратору базы данных.  
  
## <a name="see-also"></a>См. также раздел

- [Настройка отладки SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Практическое руководство. Задайте разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)