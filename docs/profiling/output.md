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
ms.openlocfilehash: 6ead4ac1f7b420ac59fc58f87d4351498148c161
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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