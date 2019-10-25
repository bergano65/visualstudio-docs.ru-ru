---
title: 'Ошибка: выполнение Transact-SQL завершено без отладки | Документация Майкрософт'
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
ms.openlocfilehash: 94ced2902becc2e988cde5198eff28911864dcbb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736937"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Ошибка: выполнение Transact-SQL завершается без отладки

Эта ошибка возникает при попытке отладки Transact-SQL или процедуры SQLCLR, когда отладчик не получает сообщения отладки от SQL Server.

Эта проблема может быть вызвана проблемами в сети или проблемами SQL Server, но наиболее вероятной причиной является проблема с разрешениями.

Принимают участие две учетные записи:

- Учетная запись приложения является учетной записью пользователя, с которой выполняется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Учетная запись соединения — это идентификация, используемая для подключения к SQL Server. Эта учетная запись не обязательно совпадает с идентификатором, который работает в Visual Studio, как если бы подключение использовало проверку подлинности SQL.

  Для отладки SQL необходимо, чтобы учетная запись приложения совпадала с учетной записью подключения или иметь роль sysadmin.

  Если вы используете имя учетной записи SQL, такое как SA, учетная запись приложения должна быть настроена на SQL Server в качестве системного администратора. По умолчанию администраторы на компьютере, на котором выполняется SQL Server, SQL Server sysadmin.

  Чтобы устранить эту ошибку, необходимо:

  - Проверить установленные параметры прав доступа. Дополнительные сведения см. [в разделе инструкции. установка SQL Server разрешений для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Удостовериться в том, что отладка SQL настроена верно.

  - Обратиться за консультацией к администратору сети или администратору базы данных.

## <a name="see-also"></a>См. также

- [Настройка отладки SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Как задать разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)