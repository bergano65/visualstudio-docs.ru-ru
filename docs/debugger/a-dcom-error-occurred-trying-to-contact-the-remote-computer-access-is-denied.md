---
title: "При попытке обращения к удаленному компьютеру возникла ошибка DCOM. Отказано в доступе. | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a861d3af9ae02fbbfc4fac2b38cc76058c8a3caf
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>При попытке обращения к удаленному компьютеру возникла ошибка DCOM. Отказано в доступе.
В перечисленных ниже случаях при выполнении удаленной отладки используется DCOM для обмена данными между локальным и удаленным компьютерами:  
  
-   Отладчик настроен **режима совместимости машинного кода** или **режим совместимости управляемого кода** возврата **Сервис > Параметры > Отладка** страницы  
  
-   Выполняется отладка управляемого кода C++ (C++/CLI).  
  
-   В Visual Studio 2013 при **включить собственный изменить и продолжить** возврата **Сервис > Параметры > Отладка** страницы  
  
-   Некоторые сценарии отладки с использованием отладчика стороннего поставщика.  
  
 Данная ошибка возникает, если процессу Visual Studio не удалось подтвердить свою подлинность при подключении к процессу удаленного отладчика через DCOM (либо предоставленные учетные данные были сочтены недостаточными). Для устранения этой проблемы можно попробовать выполнить одно или несколько следующих действий.  
  
-   Отключите  **собственный режим совместимости** и **режим совместимости управляемого кода**.  
  
-   В Visual Studio 2013 отключите **Включить собственную операцию "Изменить и продолжить"**.  
  
-   Перезагрузите оба компьютера.  
  
-   Если для удаленной отладки требуется ввод учетных данных, включите сохранение учетных данных с помощью соответствующего параметра.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)