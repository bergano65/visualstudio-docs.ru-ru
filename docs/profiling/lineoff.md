---
title: "Параметр LineOff | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6914a94300cd7fdb06db8743159698047451fd74
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="lineoff"></a>LineOff
При использовании метода профилирования с выборкой профилировщик по умолчанию собирает сведения о количестве строк исходного кода и смещении номеров строк. Параметр **LineOff** команды VSPerfCmd отключает сбор данных по номерам строк, когда команда VSPerfCmd используется для запуска приложения. Если задан параметр **LineOff**, данные профилирования собираются до уровня функции.  
  
 Параметр **LineOff** можно использовать только с параметром **Launch** и только в том случае, если профилировщик был инициализирован для выборки с помощью параметра **Start**:**Sample**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **LineOff** можно использовать только в команде, в которой также содержится параметр **Launch**.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
## <a name="example"></a>Пример  
 В этом примере запускаются приложение и профилировщик и отключается выборка на уровне строк.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)