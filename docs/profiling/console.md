---
title: Параметр Console | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04cf166880ac8bcf83d4657b9c1c2eec1b46a14a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34690820"
---
# <a name="console"></a>Консоль
Параметр **Console** программы VSPerfCmd.exe запускает указанное приложение в новом окне командной строки. Параметр **Console** можно использовать только вместе с параметром **Launch** программы VSPerfCmd. Если приложение не является приложением командной строки, параметр **Console** ни на что не влияет.  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **Console** можно указывать только в командной строке, в которой также содержится параметр **Launch**.  
  
 **Launch:** `AppName`  
 Запускает профилировщик и приложение, заданное параметром `AppName`.  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)