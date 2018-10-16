---
title: Параметр Shutdown | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fcc2012f46311d51cfd7c50f28158a471b67e26
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269301"
---
# <a name="shutdown"></a>Завершить работу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **Shutdown** обеспечивает выключение профилировщика и закрытие файла данных профилирования спустя определенное время ожидания после завершения или отключения профилируемого в данный момент процесса. Параметр **Shutdown** должен быть последней командой в сеансе профилирования.  
  
 Если параметр времени ожидания не задан, параметр **Shutdown** приводит к бесконечному ожиданию. Если параметр времени ожидания задан, этот параметр возвращается спустя заданное число секунд без выключения профилировщика или закрытия файла данных.  
  
 Параметр **Shutdown** должен быть единственным параметром в командной строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Параметры  
 `Timeout`  
 -   Если этот параметр задан, он возвращается спустя указанное число секунд без выключения профилировщика или закрытия файла данных профилирования (необязательно).  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)



