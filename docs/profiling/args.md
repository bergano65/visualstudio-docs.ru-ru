---
title: "Args | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c483cea9b174e330cd951d55eb287807d8262a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="args"></a>Args
Параметр **Args** VSPerfCmd.exe определяет список аргументов, которые передаются целевому приложению подкоманды **Launch**.  
  
 **Args** можно использовать только при условии, если в командной строке также задан параметр **Launch**. Использовать **Args** не обязательно, если указан параметр **Launch**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 `Arguments`  
 Список аргументов для целевого приложения команды **Launch**.  
  
## <a name="required-options"></a>Обязательные параметры  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование с помощью метода выборки.  
  
## <a name="example"></a>Пример  
 В следующем примере параметр **Args** используется для передачи аргументов в TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)