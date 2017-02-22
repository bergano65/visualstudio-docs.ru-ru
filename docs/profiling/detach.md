---
title: "Detach | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Detach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **Detach** программы VSPerfCmd.exe отсоединяет профилировщик от заданных процессов или от всех процессов, если процессы не заданы.  Для инициализации профилирования нужно использовать метод выборки.  
  
 Профилирование, запущенное с параметрами **Launch** или **Attach**, можно отсоединить с помощью команды **Detach**.  Для повторного присоединения профилировщика можно воспользоваться командами **Attach**.  
  
 Команда **Detach** не приводит к закрытию файла данных профилирования.  Чтобы завершить профилирование и закрыть файл данных, воспользуйтесь параметром **Shutdown**.  
  
> [!NOTE]
>  Если параметр **Start** был задан с помощью параметра **Crosssession**, все вызовы команды **VSPerfCmd \/Attach** или **VSPerfCmd \/Detach** также должны задавать параметр **Crosssession**.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### Параметры  
 `PIDs|ProcessNames`  
 `PID` — числовой идентификатор системы одного или нескольких процессов.  
  
 `ProcessNames` — имя процесса.  Если запущено несколько экземпляров именованного процесса, результат будет непредсказуемым.  
  
 Разделите процессы запятыми.  
  
 Если процесс не задан, профилировщик отсоединяется ото всех профилируемых процессов.  
  
## Допустимые параметры  
 Следующие параметры **VSPerfCmd** можно сочетать с параметром **Attach** в одной командной строке.  
  
 **Crosssession**  
 Включает приложения профилирования в сеансах, отличных от сеанса входа в систему.  Является обязательным, если параметр **Start** был задан с помощью параметра **Crosssession**.  
  
## Пример  
 В этом примере команда **Detach** отключает профилирование, а команда **Shutdown** закрывает файл данных профилировщика.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб\-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)