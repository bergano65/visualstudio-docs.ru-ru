---
title: 'Ошибка: Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
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
ms.openlocfilehash: 795dcb07459318326085d5e1fe99554d9c8d1311
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349508"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Ошибка. Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug
Хранимую процедуру sp_enable_sql_debug не удалось выполнить на сервере. Для этого могут быть следующие причины:  
  
- Проблема подключения. Подключение к серверу должно быть стабильным.  
  
- Отсутствие необходимых разрешений на сервере. Для отладки на SQL Server 2005 учетная запись, запущенная Visual Studio, и учетная запись, используемая для подключения к SQL Server, должны быть членами роли системного администратора. Учетная запись, используемая для подключения к SQL Server, является либо учетной записью Windows (при использовании проверки подлинности Windows) либо учетной записью с идентификатором пользователя и паролем (при использовании проверки подлинности SQL).  
  
  Дополнительные сведения см. в разделе [как: задать разрешения для SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>См. также  
 [Практическое: задать разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Настройка отладки SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))