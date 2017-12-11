---
title: "Параметр AutoMark | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc5ad59520f8533527f5c17f6be4b04ad860f2d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="automark"></a>Параметр AutoMark
Параметр **AutoMark** указывает интервал (в миллисекундах) между сбором событий счетчиков производительности для программного обеспечения Windows. Счетчики производительности Windows указываются в параметре **WinCounter**.  
  
 В командной строке можно указать только один параметр **AutoMark**. Обратите внимание, что интервал выборки **WinCounter**, указанный в **AutoMark**, не зависит от основного интервала выборки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### <a name="parameters"></a>Параметры  
 `Milliseconds`  
 Указывает интервал (в миллисекундах) между сбором данных счетчиков производительности Windows.  
  
## <a name="required-options"></a>Обязательные параметры  
 **WinCounter:** `Path`  
 Указывает счетчик производительности Windows, данные которого нужно собрать. При использовании метода инструментирования можно указать несколько счетчиков Windows. При использовании метода выборки можно указать всего один счетчик программного обеспечения. Параметр **WinCounter** следует указывать в командной строке, которая содержит параметр **Start**.  
  
## <a name="example"></a>Пример  
 В этом примере для двух счетчиков производительности Windows установлен интервал выборки 1000 миллисекунд.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)