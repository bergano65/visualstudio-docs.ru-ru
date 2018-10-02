---
title: Attach | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7724aa0691e26f35c429a46f570f3f80ed8dd06f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562959"
---
# <a name="attach"></a>Attach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Attach](https://docs.microsoft.com/visualstudio/profiling/attach).  
  
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
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:** Events]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]  
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



