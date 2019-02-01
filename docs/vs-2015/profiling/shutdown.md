---
title: Параметр Shutdown | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b9b8848399ea88b5f4ce7ebf30f970e2091e6406
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784603"
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
  
## <a name="see-also"></a>См. также раздел  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)
