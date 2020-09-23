---
title: RPC требуется проверка подлинности | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 9bb172455226ab290a74da07e97fc40deb30b6ba
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852554"
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Запустите `\`*windir*`\system32\regedt32.exe`.

2. Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.

4. При повторении ошибки обратитесь к администратору домена по поводу настройки групповой политики **Конфигурация компьютера > Административные шаблоны > Система > Удаленный вызов процедур (RPC) > Ограничения для не прошедших проверку подлинности RPC-клиентов**.