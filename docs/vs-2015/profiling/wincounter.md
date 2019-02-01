---
title: WinCounter | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9424eb099516761866ec459888ff830fcf56a28b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791568"
---
# <a name="wincounter"></a>WinCounter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **WinCounter** задает счетчик производительности Windows или приложения, данные которого собираются через указанные интервалы в течение сеанса профилирования. Счетчики производительности Windows и приложений перечисляются в виде меток в файле данных профилирования. Можно задать несколько счетчиков производительности, данные которых необходимо собирать, воспользовавшись отдельными параметрами.  
  
 По умолчанию данные счетчиков собираются каждые 500 миллисекунд. С помощью параметра **AutoMark** можно задать другой интервал сбора данных.  
  
 Используется только один параметр **AutoMark**. Если указаны несколько параметров **AutoMark**, используется последний из них.  
  
 Параметр **WinCounter** можно использовать только вместе с параметром **Start**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 `Path`  
 Счетчик производительности Windows в формате пути счетчика PDH.  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **WinCounter** можно использовать только вместе с параметром **Start**.  
  
 **Start:** `Method`  
 Параметр **Start** инициализирует профилировщик для заданного метода профилирования.  
  
## <a name="exclusive-options"></a>Монопольные параметры  
 Параметр **AutoMark** можно использовать только вместе с параметром **WinCounter**.  
  
 **AutoMark:** `Milliseconds`  
 Задает интервал времени (в миллисекундах) между сбором данных счетчика производительности Windows.  
  
## <a name="example"></a>Пример  
 В этом примере задан сбор данных двух счетчиков производительности Windows с интервалом 1000 миллисекунд.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>См. также раздел  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)
