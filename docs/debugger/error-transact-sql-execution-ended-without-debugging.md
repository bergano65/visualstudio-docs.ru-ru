---
title: 'Ошибка: Выполнение Transact-SQL завершается без отладки | Документация Майкрософт'
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
ms.openlocfilehash: 71d1f14bef8eb69fa6c6fc4d9c3f669826079c99
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722347"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Ошибка: выполнение Transact-SQL завершается без отладки

Эта ошибка возникает при попытке отладки Transact-SQL или процедуры SQLCLR и отладчик не получает сообщения об отладке от SQL Server.

Эта проблема может быть следствием сетевых проблем или проблем на сервере SQL Server, но наиболее вероятной причиной является проблема с разрешениями.

Принимают участие две учетные записи:

- Учетная запись приложения является учетной записью пользователя, с которой выполняется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Учетная запись соединения — это идентификация, используемая для подключения к SQL Server. Эта учетная запись не обязательно совпадают с учетными данными, на котором выполняется Visual Studio, как, если соединение использует проверку подлинности SQL.

  Отладка SQL требует учетной записи приложения должен соответствовать учетной записи подключения или входить в роль sysadmin.

  Если вы используете имя учетной записи SQL, например sa, учетной записи приложений должны настраиваться в SQL Server как учетная запись администратора. По умолчанию Администраторы на компьютере под управлением SQL server, являются администраторами SQL Server.

  Чтобы устранить эту ошибку, необходимо:

  - Проверить установленные параметры прав доступа. Дополнительные сведения см. в разделе [как: задать разрешения для SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Удостовериться в том, что отладка SQL настроена верно.

  - Обратиться за консультацией к администратору сети или администратору базы данных.

## <a name="see-also"></a>См. также раздел

- [Настройка отладки SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Практическое: задать разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)