---
title: 'Ошибка: Брандмауэр без проверки подлинности | Документы Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db13165c584399952dc491cf714ac84ee4de7598
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697431"
---
# <a name="error-firewall-no-authentication"></a>Ошибка: брандмауэр без проверки подлинности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Брандмауэр подключения к Интернету на удаленном компьютере не настроен для удаленной отладки. Для удаленной отладки в режиме `No Authentication` в список исключений должен быть добавлен исполняемый файл msvsmon.exe. Возможно также потребуется открыть некоторые порты IPSec.  
  
> [!NOTE]
> Удаленный отладчик может автоматически настроить межсетевой экран Windows. Если вместо межсетевого экрана Windows используется другой межсетевой экран, например программный или аппаратный межсетевой экран другого производителя, его необходимо настроить вручную, чтобы он допускал выполнение удаленной отладки. Для этого необходимо разрешить трафик через порты TCP/IP, прослушиваемые программой msvsmon.exe. По умолчанию это порты 4018 и 4019, при этом порт 4018 используется во всех операционных системам, тогда как порт 4019 используется только в Windows x64 для разрешения отладки процессов x86.  
  
 Дополнительные сведения см. в разделе [настройка удаленные средства на устройстве](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
