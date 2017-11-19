---
title: "Ошибка: RPC требуется проверка подлинности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3431ee286787d99e8601fbed7cad3012ffcaf68e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Запустите `\` *windir*`\system32\regedt32.exe`  
  
2.  Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.  
  
4.  Если ошибка повторится, обратитесь к администратору домена о **Конфигурация компьютера > Административные шаблоны > Система > удаленный вызов процедуры > ограничения для не прошедших проверку подлинности RPC-клиент** Групповая политика значение параметра.