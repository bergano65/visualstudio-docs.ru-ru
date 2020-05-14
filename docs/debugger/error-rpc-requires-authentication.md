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
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850454"
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Запустите `\`*windir*`\system32\regedt32.exe`.

2. Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.

4. При повторении ошибки обратитесь к администратору домена по поводу настройки групповой политики **Конфигурация компьютера > Административные шаблоны > Система > Удаленный вызов процедур (RPC) > Ограничения для не прошедших проверку подлинности RPC-клиентов**.