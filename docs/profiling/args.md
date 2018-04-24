---
title: Args | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c92cde3389710e292d8f6b24625055065a9128a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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