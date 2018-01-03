---
title: "Параметр CrossSession | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 079e0ec1b2bad2ca01a698c474c37de6d5d7dfd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="crosssession"></a>Параметр CrossSession
Параметр VSPerfCmd.exe **CrossSession** позволяет профилировщику собирать данные из любого консольного сеанса. Параметр **CrossSession** используется с параметром **Start**.  
  
 Вместо **CrossSession** можно использовать сокращение **CS**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="valid-options"></a>Допустимые параметры  
 Чтобы включить профилирование в рамках другого сеанса, необходимо указать параметр **CrossSession** с параметром **Start**. **CrossSession** также необходимо указать в любой последующей команде **VSPerfCmd Attach** или **Detach**.  
  
 **Start:** `Method`  
 Параметр **Start** инициализирует профилировщик для заданного метода профилирования.  
  
 **Attach:** *PID*[**,***PID*]  
 Начинает профилирование указанных процессов.  
  
 **Detach**[**:***PID*[,*PID*]]  
 Останавливает профилирование указанных процессов.  
  
## <a name="example"></a>Пример  
 В этом примере параметр **CrossSession** используется для присоединения к приложению, запущенному в другом консольном сеансе.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)