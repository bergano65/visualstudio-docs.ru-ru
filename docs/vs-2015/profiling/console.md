---
title: Параметр Console | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1117bf7113743bfd8db63353a5b032c869a97c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558674"
---
# <a name="console"></a>Консоль
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [консоли](https://docs.microsoft.com/visualstudio/profiling/console).  
  
Параметр **Console** программы VSPerfCmd.exe запускает указанное приложение в новом окне командной строки. Параметр **Console** можно использовать только вместе с параметром **Launch** программы VSPerfCmd. Если приложение не является приложением командной строки, параметр **Console** ни на что не влияет.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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



