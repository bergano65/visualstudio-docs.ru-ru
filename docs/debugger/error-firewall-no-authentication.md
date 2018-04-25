---
title: 'Ошибка: Брандмауэр без проверки подлинности | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ca9603b7b678eb288b78d09f62cc8aac5774ebc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="error-firewall-no-authentication"></a>Ошибка: брандмауэр без проверки подлинности
Брандмауэр подключения к Интернету на удаленном компьютере не настроен для удаленной отладки. Для удаленной отладки в режиме `No Authentication` в список исключений должен быть добавлен исполняемый файл msvsmon.exe. Возможно также потребуется открыть некоторые порты IPSec.  
  
> [!NOTE]
>  Удаленный отладчик может автоматически настроить межсетевой экран Windows. Если вместо межсетевого экрана Windows используется другой межсетевой экран, например программный или аппаратный межсетевой экран другого производителя, его необходимо настроить вручную, чтобы он допускал выполнение удаленной отладки. Для этого необходимо разрешить трафик через порты TCP/IP, прослушиваемые программой msvsmon.exe. По умолчанию это порты 4018 и 4019, при этом порт 4018 используется во всех операционных системам, тогда как порт 4019 используется только в Windows x64 для разрешения отладки процессов x86.  
  
 Дополнительные сведения см. в разделе [удаленной отладки](../debugger/remote-debugging.md).