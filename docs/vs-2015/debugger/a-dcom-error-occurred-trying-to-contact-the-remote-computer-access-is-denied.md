---
title: При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе. | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993584"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В перечисленных ниже случаях при выполнении удаленной отладки используется DCOM для обмена данными между локальным и удаленным компьютерами:  
  
- Для отладчика задан **собственный режим совместимости** или же установлен флажок **Режим совместимости управляемого кода** на странице **Сервис -&gt; Параметры -&gt; Отладка** .  
  
- Выполняется отладка управляемого кода C++ (C++/CLI).  
  
- В Visual Studio 2013, если установлен флажок **Включить собственную операцию "Изменить и продолжить"** на странице **Сервис -&gt; Параметры -&gt; Отладка** .  
  
- Некоторые сценарии отладки с использованием отладчика стороннего поставщика.  
  
  Данная ошибка возникает, если процессу Visual Studio не удалось подтвердить свою подлинность при подключении к процессу удаленного отладчика через DCOM (либо предоставленные учетные данные были сочтены недостаточными). Для устранения этой проблемы можно попробовать выполнить одно или несколько следующих действий.  
  
- Отключите  **собственный режим совместимости** и **режим совместимости управляемого кода**.  
  
- В Visual Studio 2013 отключите **Включить собственную операцию "Изменить и продолжить"**.  
  
- Перезагрузите оба компьютера.  
  
- Если для удаленной отладки требуется ввод учетных данных, включите сохранение учетных данных с помощью соответствующего параметра.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
