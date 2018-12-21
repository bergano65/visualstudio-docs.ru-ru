---
title: Параметр LineOff | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93fe4acedfcae36f75ed38bef102ccc35f08f2ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759675"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



