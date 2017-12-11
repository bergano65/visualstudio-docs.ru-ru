---
title: "Attach | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbba99fd39bff8364e7853cd8d0f73f0e567e1d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="attach"></a>Attach
Параметр **Attach** программы VSPerfCmd.exe начинает профилирование с выборкой для запущенного процесса, указанного идентификатором процесса (PID).  
  
 Для использования параметра **Attach** нужно указать метод **Sample** в параметре Start.  
  
> [!NOTE]
>  Если параметр **Start** был задан с параметром **Crosssession**, во всех вызовах команды **VSPerfCmd /Attach** или **VSPerfCmd /Detach** также должен быть указан параметр **Crosssession**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 `ProcessID`  
 Идентификатор процесса (PID) для запущенного процесса. Идентификатор запущенного процесса указан на вкладке "Процессы" диспетчера задач Windows.  
  
## <a name="valid-options"></a>Допустимые параметры  
 Указанные ниже параметры программы **VSPerfCmd** могут сочетаться с параметром **Attach** в одной командной строке.  
  
 **Crosssession**  
 Включает профилирование приложений в сеансах, отличных от сеанса входа в систему. Является обязательным, если параметр **Start** был задан с параметром **Crosssession**.  
  
 **Start:** `Method`  
 Инициализирует сеанс командной строки для профилировщика и задает метод профилирования.  
  
 **TargetCLR**  
 Указывает версию профилируемой среды CLR, если в рамках сеанса профилирования загружено несколько версий. По умолчанию профилируется первая загруженная версия.  
  
 **GlobalOn GlobalOff**  
 Возобновляет (**GlobalOn**) или приостанавливает (**GlobalOff**) профилирование, но не завершает сеанс профилирования.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Возобновляет (**ProcessOn**) или приостанавливает (**ProcessOff**) профилирование для указанного процесса.  
  
## <a name="interval-options"></a>Параметры интервала  
 В командной строке с параметром "Attach" можно задать один из указанных ниже параметров интервала выборки. Интервал выборки по умолчанию равен 10 000 000 циклам тактовой частоты процессора.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]  
 Задает числовое значение и тип интервала выборки.  
  
-   **Timer** — осуществляет выборку через каждые `Cycles` циклов тактовой частоты процессора. Если параметр `Cycles` не задан, используется значение 10 000 000 циклов.  
  
-   **PF** — осуществляет выборку через каждые `Events` ошибок страницы. Если параметр `Events` не задан, выборка осуществляется через каждые 10 ошибок страницы.  
  
-   **Sys** — осуществляет выборку через каждые `Events` вызовов операционной системы. Если параметр `Events` не задан, выборка осуществляется через каждые 10 системных вызовов.  
  
-   **Counter** — осуществляет выборку через каждое значение `Reload` счетчика производительности ЦП, указанное в параметре `Name`. Кроме того, в параметре `FriendlyName` можно задать строку, используемую в качестве заголовка столбца в отчетах профилировщика.  
  
## <a name="example"></a>Пример  
 Этот пример показывает, как подключиться к запущенному экземпляру приложения с идентификатором процесса 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)