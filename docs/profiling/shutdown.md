---
title: Параметр Shutdown | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 435011200065f1f27ff54c14c57d71eb651fd8e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952077"
---
# <a name="shutdown"></a>Завершить работу
Параметр **Shutdown** обеспечивает выключение профилировщика и закрытие файла данных профилирования спустя определенное время ожидания после завершения или отключения профилируемого в данный момент процесса. Параметр **Shutdown** должен быть последней командой в сеансе профилирования.  
  
 Если параметр времени ожидания не задан, параметр **Shutdown** приводит к бесконечному ожиданию. Если параметр времени ожидания задан, он возвращается спустя заданное число секунд без выключения профилировщика или закрытия файла данных.  
  
 Параметр **Shutdown** должен быть единственным параметром в командной строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
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