---
title: Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug | Документация Майкрософт
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
ms.openlocfilehash: c8131c7b16205b308e04b621dd1fcb536ba94c14
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852430"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Ошибка: Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug

Хранимую процедуру sp_enable_sql_debug не удалось выполнить на сервере. Для этого могут быть следующие причины:

- Проблема подключения. Подключение к серверу должно быть стабильным.

- Отсутствие необходимых разрешений на сервере. Для отладки на SQL Server 2005 учетная запись, запущенная Visual Studio, и учетная запись, используемая для подключения к SQL Server, должны быть членами роли системного администратора. Учетная запись, используемая для подключения к SQL Server, является либо учетной записью Windows (при использовании проверки подлинности Windows) либо учетной записью с идентификатором пользователя и паролем (при использовании проверки подлинности SQL).

Дополнительные сведения см. в разделе [Практическое руководство. Предоставление разрешений на отладку SQL Server](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>См. также

- [Практическое руководство. Предоставление разрешений на отладку SQL Server](/previous-versions/w1bhybwz(v=vs.100))
- [Настройка отладки SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))