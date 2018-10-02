---
title: GC (VSPerfCmd) | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e7323d679ac0cde2a1227c1c9ce4b7e3a380fd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571011"
---
# <a name="gc-vsperfcmd"></a>Параметр GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [GC (VSPerfCmd)](https://docs.microsoft.com/visualstudio/profiling/gc-vsperfcmd).  
  
Параметр **GC** включает сбор данных о выделении памяти и времени существования объектов. Параметр **GC** можно использовать только с методом профилирования с выборкой и только с параметром **Launch**.  
  
 При использовании параметра **GC** команда VSPerfClrEnv **/sampleon** не требуется.  
  
 Если параметры не указаны или указан параметр **Allocation**, собираются только данные о выделения памяти .NET Framework. Если указан параметр **Lifetime**, собираются данные о выделении памяти и времени существования объектов .NET Framework.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 **Allocation**  
 По умолчанию. Собирает данные о выделении памяти .NET Framework.  
  
 **Время существования**  
 Собирает данные о выделении памяти и времени существования объектов .NET Framework.  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **GC** может использоваться только с параметром **Launch**.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
## <a name="example"></a>Пример  
 Следующий пример запускает приложение и собирает данные о выделении памяти .NET Framework.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)



