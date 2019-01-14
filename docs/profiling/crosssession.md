---
title: Параметр CrossSession | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 192ddfb7312dff13b457f36940220f0bb17fe2c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909259"
---
# <a name="crosssession"></a>Параметр CrossSession
Параметр *VSPerfCmd.exe* **CrossSession** позволяет профилировщику собирать данные из любого консольного сеанса. Параметр **CrossSession** используется с параметром **Start**.  
  
 Вместо **CrossSession** можно использовать сокращение **CS**.  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="valid-options"></a>Допустимые параметры  
 Чтобы включить профилирование в рамках другого сеанса, необходимо указать параметр **CrossSession** с параметром **Start**. **CrossSession** также необходимо указать в любой последующей команде **VSPerfCmd Attach** или **Detach**.  
  
 **Start:** `Method`  
 Параметр **Start** инициализирует профилировщик для заданного метода профилирования.  
  
 **Attach:** _PID_[**,**_PID_]  
 Начинает профилирование указанных процессов.  
  
 **Detach**[**:**_PID_[,_PID_]]  
 Останавливает профилирование указанных процессов.  
  
## <a name="example"></a>Пример  
 В этом примере параметр **CrossSession** используется для присоединения к приложению, запущенному в другом консольном сеансе.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)