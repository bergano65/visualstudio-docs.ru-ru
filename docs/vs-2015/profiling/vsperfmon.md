---
title: VSPerfMon | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a06a6632d62f853eef33cad00ad766e0d1aab87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184012"
---
# <a name="vsperfmon"></a>VSPerfMon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Средство VSPerfMon используется с целью сбора данных производительности для приложения. Как правило, оно запускается средством VSPerfCmd.exe. VSPerfMon выводит дополнительные сведения о присоединении или отсоединении процессов, недоступные при использовании средства VSPerfCmd. Для просмотра этих сведений средство VSPerfMon следует запустить в отдельном окне. Для вызова VSPerfMon используется следующий синтаксис:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 В приведенной ниже таблице описываются параметры средства VSPerfMon.  
  
|Параметры|ОПИСАНИЕ|  
|-------------|-----------------|  
|**U**|Перенаправленный вывод на консоль записывается в кодировке Юникода.  Этот параметр следует указывать первым.|  
|**OUTPUT:** `<` *имя файла* `>`|Перенаправление выходных данных в файл с указанным именем.|  
|**TRACE**|Запуск системного монитора для профилирования с инструментированием.|  
|**SAMPLE**|Запуск монитора производительности для профилирования с выборкой.|  
|**COVERAGE**|Запуск монитора производительности для сбора данных об объеме протестированного кода.|  
|**CONCURRENCY**|Запуск системного монитора для профилирования состязаний за ресурсы.|  
|**USER:** `[` *домен* `\]` *имя_пользователя*|Позволяет клиенту получать доступ к системному монитору с помощью указанной учетной записи.|  
|**CROSSSESSION**|Включает профилирования в нескольких сеансах.|  
|**COUNTER** `:cfg`|При использовании метода профилирования с инструментированием (TRACE) указывает счетчик ЦП, значение которого требуется собирать в каждой точке инструментирования. Можно собирать данные от нескольких счетчиков, задав несколько параметров Counter.<br /><br /> Используйте следующий синтаксис для описания данных счетчика (*cfg*):<br /><br /> **CounterName** [ **,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** — это имя счетчика, которое возвращается командой VSPerfCmd /QueryCounters.<br />-   **Reload** определяет интервал выборки событий счетчика. Не используйте *Reload* с методом инструментирования.<br />Если указано значение **FriendlyName**, оно заменяет **CounterName** в именах столбцов отчетов средств профилирования.|  
|**WINCOUNTER** `:path`|Задает счетчик производительности Windows, который следует включить в данные меток. `path` — это строка счетчика производительности Windows в формате пути к счетчику PDH. Например:<br /><br /> \Processor(0)\\% процессорного времени<br /><br /> \System\Контекстных переключений/с|  
|**AUTOMARK** `:n`|Указывает временной интервал (в миллисекундах) между автоматическими метками при использовании параметра /WINCOUNTER. Округляется до ближайшего значения, кратного 500 мс.<br /><br /> Для отключения автоматических меток используется значение 0 (если значение не указано, используется значение 500 мс).|  
  
## <a name="see-also"></a>См. также  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Представления отчетов о производительности](../profiling/performance-report-views.md)
