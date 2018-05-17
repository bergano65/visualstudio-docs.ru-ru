---
title: VSPerfMon | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: be865f9fe51a1028192d54de556a52e47b241f0d
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="vsperfmon"></a>VSPerfMon
Средство VSPerfMon используется с целью сбора данных производительности для приложения. Как правило, оно запускается средством VSPerfCmd.exe. VSPerfMon выводит дополнительные сведения о присоединении или отсоединении процессов, недоступные при использовании средства VSPerfCmd. Для просмотра этих сведений средство VSPerfMon следует запустить в отдельном окне. Для вызова VSPerfMon используется следующий синтаксис:  
  
```cmd  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 В приведенной ниже таблице описываются параметры средства VSPerfMon.  
  
|Параметры|Описание:|  
|-------------|-----------------|  
|**U**|Перенаправленный вывод на консоль записывается в кодировке Юникода.  Этот параметр следует указывать первым.|  
|**OUTPUT:** `<` *имя файла* `>`|Перенаправление выходных данных в файл с указанным именем.|  
|**TRACE**|Запуск системного монитора для профилирования с инструментированием.|  
|**SAMPLE**|Запуск монитора производительности для профилирования с выборкой.|  
|**COVERAGE**|Запуск монитора производительности для сбора данных об объеме протестированного кода.|  
|**CONCURRENCY**|Запуск системного монитора для профилирования состязаний за ресурсы.|  
|**USER:** `[` *домен* `\]` *имя_пользователя*|Позволяет клиенту получать доступ к системному монитору с помощью указанной учетной записи.|  
|**CROSSSESSION**|Включает профилирования в нескольких сеансах.|  
|**COUNTER** `:cfg`|При использовании метода профилирования с инструментированием (TRACE) указывает счетчик ЦП, значение которого требуется собирать в каждой точке инструментирования. Можно собирать данные от нескольких счетчиков, задав несколько параметров Counter.<br /><br /> Используйте следующий синтаксис для описания данных счетчика (*cfg*):<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** — это имя счетчика, которое возвращается командой VSPerfCmd /QueryCounters.<br />-   **Reload** определяет интервал выборки событий счетчика. Не используйте *Reload* с методом инструментирования.<br />Если указано значение **FriendlyName**, оно заменяет **CounterName** в именах столбцов отчетов средств профилирования.|  
|**WINCOUNTER** `:path`|Задает счетчик производительности Windows, который следует включить в данные меток. `path` — это строка счетчика производительности Windows в формате пути к счетчику PDH. Пример:<br /><br /> \Processor(0)\\% процессорного времени<br /><br /> \System\Контекстных переключений/с|  
|**AUTOMARK** `:n`|Указывает временной интервал (в миллисекундах) между автоматическими метками при использовании параметра /WINCOUNTER. Округляется до ближайшего значения, кратного 500 мс.<br /><br /> Для отключения автоматических меток используется значение 0 (если значение не указано, используется значение 500 мс).|  
  
## <a name="see-also"></a>См. также  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Представления отчетов о производительности](../profiling/performance-report-views.md)