---
title: При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе. | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cabac4997480b626714c129daef0511643ae2a50
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570787"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [DCOM-ошибка при попытке подключиться к удаленному компьютеру. Доступ запрещен. ](https://docs.microsoft.com/visualstudio/debugger/a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied).  
  
В перечисленных ниже случаях при выполнении удаленной отладки используется DCOM для обмена данными между локальным и удаленным компьютерами:  
  
-   Для отладчика задан **собственный режим совместимости** или же установлен флажок **Режим совместимости управляемого кода** на странице **Сервис -&gt; Параметры -&gt; Отладка** .  
  
-   Выполняется отладка управляемого кода C++ (C++/CLI).  
  
-   В Visual Studio 2013, если установлен флажок **Включить собственную операцию "Изменить и продолжить"** на странице **Сервис -&gt; Параметры -&gt; Отладка** .  
  
-   Некоторые сценарии отладки с использованием отладчика стороннего поставщика.  
  
 Данная ошибка возникает, если процессу Visual Studio не удалось подтвердить свою подлинность при подключении к процессу удаленного отладчика через DCOM (либо предоставленные учетные данные были сочтены недостаточными). Для устранения этой проблемы можно попробовать выполнить одно или несколько следующих действий.  
  
-   Отключите  **собственный режим совместимости** и **режим совместимости управляемого кода**.  
  
-   В Visual Studio 2013 отключите **Включить собственную операцию "Изменить и продолжить"**.  
  
-   Перезагрузите оба компьютера.  
  
-   Если для удаленной отладки требуется ввод учетных данных, включите сохранение учетных данных с помощью соответствующего параметра.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)



