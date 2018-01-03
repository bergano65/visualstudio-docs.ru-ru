---
title: "Параметр Output | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b7452ad6aa8d7f190eebbc35d4be087c14dcd51a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="output"></a>Вывод
Параметр **Output** задает имя файла данных профилирования для сеанса профилирования. Параметр **Output** должен использоваться с параметром **Start**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 `FileName`  
 Имя файла данных. Допускаются полные или частичные пути. Если путь не указан, файл создается в текущем каталоге.  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **Output** используется с параметром **Start**.  
  
 **Start:** `Method`  
 Задает имя выходного файла.  
  
## <a name="example"></a>Пример  
 В этом примере файл данных профилирования создается в текущем каталоге.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)