---
title: Параметр Shutdown | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1a9c79b132dcd3358c697f9b08466af306aeed21
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="shutdown"></a>Завершить работу
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