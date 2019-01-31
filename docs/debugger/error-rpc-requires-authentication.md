---
title: 'Ошибка: RPC требуется проверка подлинности | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
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
ms.openlocfilehash: ffe83a83504d6de05e25abe9350bb9553912c4f2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943764"
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Запустите `\` *windir*`\system32\regedt32.exe`  
  
2.  Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.  
  
4.  Если проблема сохранится, обратитесь к администратору домена о **Конфигурация компьютера > Административные шаблоны > Система > удаленный вызов процедуры > ограничения для не прошедших проверку подлинности RPC-клиентов** Групповая политика значение параметра.