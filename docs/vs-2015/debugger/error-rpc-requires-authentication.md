---
title: 'Ошибка: RPC требуется проверка подлинности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3393e5a70a0662d15cc4d643f7a5df106860d26
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990935"
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Запустите `\` *windir*`\system32\regedt32.exe`  
  
2.  Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.  
  
4.  Если проблема сохранится, обратитесь к администратору домена о **Конфигурация компьютера -> Административные шаблоны - > Система -> удаленный вызов процедуры "->" ограничения для не прошедших проверку подлинности RPC-клиентов** группы параметр политики.
