---
title: 'Ошибка: пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84326c5c1beb91269a5f097c8c5d7cb8782a7a56
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600153"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Ошибка: Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug

Хранимую процедуру sp_enable_sql_debug не удалось выполнить на сервере. Для этого могут быть следующие причины:

- Проблема подключения. Подключение к серверу должно быть стабильным.

- Отсутствие необходимых разрешений на сервере. Для отладки на SQL Server 2005 учетная запись, запущенная Visual Studio, и учетная запись, используемая для подключения к SQL Server, должны быть членами роли системного администратора. Учетная запись, используемая для подключения к SQL Server, является либо учетной записью Windows (при использовании проверки подлинности Windows) либо учетной записью с идентификатором пользователя и паролем (при использовании проверки подлинности SQL).

Дополнительные сведения см. в разделе [Практическое руководство. Предоставление разрешений на отладку SQL Server](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>См. также

- [Практическое руководство. Предоставление разрешений на отладку SQL Server](/previous-versions/w1bhybwz(v=vs.100))
- [Настройка отладки SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))