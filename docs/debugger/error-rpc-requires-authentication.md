---
title: "Ошибка: RPC требуется проверка подлинности | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: RPC требуется проверка подлинности
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отладчику Visual Studio не удается подключиться к удаленному компьютеру.  На локальном компьютере включена политика RPC, запрещающая удаленную отладку.  
  
### Исправление ошибки  
  
1.  Выполните `\`*windir*`\system32\regedt32.exe`  
  
2.  Найдите и удалите раздел реестра `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.  
  
4.  При повторении ошибки обратитесь к администратору домена по поводу настройки групповой политики Конфигурация компьютера\-\>Административные шаблоны\-\>Система\-\>Удаленный вызов процедур \(RPC\)\-\>Ограничения для не прошедших проверку подлинности RPC\-клиентов.