---
title: WinCounter | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51cb5aa0a41f311ea9c24a4ed512d6df4fe2e10f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875223"
---
# <a name="wincounter"></a>WinCounter
Параметр **WinCounter** задает счетчик производительности Windows или приложения, данные которого собираются через указанные интервалы в течение сеанса профилирования. Счетчики производительности Windows и приложений перечисляются в виде меток в файле данных профилирования. Можно задать несколько счетчиков производительности, данные которых необходимо собирать, воспользовавшись отдельными параметрами.  
  
 По умолчанию данные счетчиков собираются каждые 500 миллисекунд. С помощью параметра **AutoMark** можно задать другой интервал сбора данных.  
  
 Используется только один параметр **AutoMark**. Если указаны несколько параметров **AutoMark**, используется последний из них.  
  
 Параметр **WinCounter** можно использовать только вместе с параметром **Start**.  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)