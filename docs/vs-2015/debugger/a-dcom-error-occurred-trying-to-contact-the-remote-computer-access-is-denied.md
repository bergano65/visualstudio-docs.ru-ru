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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156533"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В перечисленных ниже случаях при выполнении удаленной отладки используется DCOM для обмена данными между локальным и удаленным компьютерами:  
  
- Для отладчика установлен **режим совместимости машинного кода** или **режим совместимости с управляемым** кодом установлен на странице " **Сервис/параметры/Отладка** ".  
  
- Выполняется отладка управляемого кода C++ (C++/CLI).  
  
- В Visual Studio 2013 при **включении собственного режима "изменить и продолжить"** на странице " **Сервис/параметры/Отладка** "  
  
- Некоторые сценарии отладки с использованием отладчика стороннего поставщика.  
  
  Данная ошибка возникает, если процессу Visual Studio не удалось подтвердить свою подлинность при подключении к процессу удаленного отладчика через DCOM (либо предоставленные учетные данные были сочтены недостаточными). Для устранения этой проблемы можно попробовать выполнить одно или несколько следующих действий.  
  
- Отключите  **собственный режим совместимости** и **режим совместимости управляемого кода**.  
  
- В Visual Studio 2013 отключите **Включить собственную операцию "Изменить и продолжить"** .  
  
- Перезагрузите оба компьютера.  
  
- Если для удаленной отладки требуется ввод учетных данных, включите сохранение учетных данных с помощью соответствующего параметра.  
  
## <a name="see-also"></a>См. также:  
 [Ошибки удаленной отладки и устранение неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
