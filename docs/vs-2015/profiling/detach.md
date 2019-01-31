---
title: Параметр Detach | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1262e88055fceef0b2170c304c8ff646eea07205
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793078"
---
# <a name="detach"></a>Detach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **Detach** программы VSPerfCmd.exe отключает профилировщик от заданных процессов или от всех процессов, если процессы не заданы. Для инициализации профилирования нужно использовать метод выборки.  
  
 Профилирование, запущенное с параметром **Launch** или **Attach**, можно отключить с помощью параметра **Detach**. Для повторного подключения профилировщика можно воспользоваться командами **Attach**.  
  
 Параметр **Detach** не приводит к закрытию файла данных профилирования. Чтобы завершить профилирование и закрыть файл данных, воспользуйтесь параметром **Shutdown**.  
  
> [!NOTE]
>  Если параметр **Start** был задан с параметром **Crosssession**, во всех вызовах команды **VSPerfCmd /Attach** или **VSPerfCmd /Detach** также должен быть указан параметр **Crosssession**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### <a name="parameters"></a>Параметры  
 `PIDs|ProcessNames`  
 `PID` — числовой системный идентификатор одного или нескольких процессов.  
  
 `ProcessNames` — имя процесса. Если запущено несколько экземпляров именованного процесса, результат будет непредсказуемым.  
  
 Разделяйте процессы запятыми.  
  
 Если процесс не задан, профилировщик отключится от всех профилируемых процессов.  
  
## <a name="valid-options"></a>Допустимые параметры  
 Указанные ниже параметры программы **VSPerfCmd** могут сочетаться с параметром **Attach** в одной командной строке.  
  
 **Crosssession**  
 Включает профилирование приложений в сеансах, отличных от сеанса входа в систему. Является обязательным, если параметр **Start** был задан с параметром **Crosssession**.  
  
## <a name="example"></a>Пример  
 В этом примере команда **Detach** приостанавливает профилирование, а команда **Shutdown** закрывает файл данных профилировщика.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## <a name="see-also"></a>См. также раздел  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)
