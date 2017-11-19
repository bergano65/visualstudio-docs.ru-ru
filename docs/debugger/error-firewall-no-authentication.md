---
title: "Ошибка: Брандмауэр без проверки подлинности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1750c0ab8bafe53136d01ba27ada9c242b318c3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-firewall-no-authentication"></a>Ошибка: брандмауэр без проверки подлинности
Брандмауэр подключения к Интернету на удаленном компьютере не настроен для удаленной отладки. Для удаленной отладки в режиме `No Authentication` в список исключений должен быть добавлен исполняемый файл msvsmon.exe. Возможно также потребуется открыть некоторые порты IPSec.  
  
> [!NOTE]
>  Удаленный отладчик может автоматически настроить межсетевой экран Windows. Если вместо межсетевого экрана Windows используется другой межсетевой экран, например программный или аппаратный межсетевой экран другого производителя, его необходимо настроить вручную, чтобы он допускал выполнение удаленной отладки. Для этого необходимо разрешить трафик через порты TCP/IP, прослушиваемые программой msvsmon.exe. По умолчанию это порты 4018 и 4019, при этом порт 4018 используется во всех операционных системам, тогда как порт 4019 используется только в Windows x64 для разрешения отладки процессов x86.  
  
 Дополнительные сведения см. в разделе [удаленной отладки](../debugger/remote-debugging.md).