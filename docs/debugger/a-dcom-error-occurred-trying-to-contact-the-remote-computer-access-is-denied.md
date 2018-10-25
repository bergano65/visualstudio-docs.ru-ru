---
title: При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе. | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 193c93e7c29d3ea9fa13c08c9d77e4e88026d814
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49900518"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>При попытке обращения к удаленному компьютеру произошла непредвиденная ошибка DCOM. Отказано в доступе.
В перечисленных ниже случаях при выполнении удаленной отладки используется DCOM для обмена данными между локальным и удаленным компьютерами:  
  
- Отладчик настроен на **собственный режим совместимости** или **режим совместимости управляемого кода** возвратом **Сервис > Параметры > Отладка** страницы  
  
- Выполняется отладка управляемого кода C++ (C++/CLI).  
  
- В Visual Studio 2013 при **включить собственный изменить и продолжить** проверяется **Сервис > Параметры > Отладка** страницы  
  
- Некоторые сценарии отладки с использованием отладчика стороннего поставщика.  
  
  Данная ошибка возникает, если процессу Visual Studio не удалось подтвердить свою подлинность при подключении к процессу удаленного отладчика через DCOM (либо предоставленные учетные данные были сочтены недостаточными). Для устранения этой проблемы можно попробовать выполнить одно или несколько следующих действий.  
  
- Отключите  **собственный режим совместимости** и **режим совместимости управляемого кода**.  
  
- В Visual Studio 2013 отключите **Включить собственную операцию "Изменить и продолжить"**.  
  
- Перезагрузите оба компьютера.  
  
- Если для удаленной отладки требуется ввод учетных данных, включите сохранение учетных данных с помощью соответствующего параметра.  
  
## <a name="see-also"></a>См. также  
 [Ошибки удаленной отладки и устранения неполадок](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)