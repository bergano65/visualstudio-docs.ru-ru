---
title: 'Ошибка: Не удалось выполнить хранимую процедуру sp_enable_sql_debug пользователя | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 759386728283d3d39219133e53668afe3259714a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697677"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>Ошибка: Пользователю не удалось выполнить хранимую процедуру sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Хранимую процедуру sp_enable_sql_debug не удалось выполнить на сервере. Для этого могут быть следующие причины:  
  
- Проблема подключения. Подключение к серверу должно быть стабильным.  
  
- Отсутствие необходимых разрешений на сервере. Для отладки на SQL Server 2005 учетная запись, запущенная Visual Studio, и учетная запись, используемая для подключения к SQL Server, должны быть членами роли системного администратора. Учетная запись, используемая для подключения к SQL Server, является либо учетной записью Windows (при использовании проверки подлинности Windows) либо учетной записью с идентификатором пользователя и паролем (при использовании проверки подлинности SQL).  
  
  Дополнительные сведения см. в разделе [Практическое руководство. Задайте разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Задайте разрешения SQL Server для отладки](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Настройка отладки SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
