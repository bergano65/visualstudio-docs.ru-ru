---
title: Параметр CrossSession | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05e1f2360b3257e44fde1af8be3554dd7fd95115
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537188"
---
# <a name="crosssession"></a>Параметр CrossSession
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр VSPerfCmd.exe **CrossSession** позволяет профилировщику собирать данные из любого консольного сеанса. Параметр **CrossSession** используется с параметром **Start**.  
  
 Вместо **CrossSession** можно использовать сокращение **CS**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствуют  
  
## <a name="valid-options"></a>Допустимые параметры  
 Чтобы включить профилирование в рамках другого сеанса, необходимо указать параметр **CrossSession** с параметром **Start**. **CrossSession** также необходимо указать в любой последующей команде **VSPerfCmd Attach** или **Detach**.  
  
 **Начало работы:**`Method`  
  Параметр **Start** инициализирует профилировщик для заданного метода профилирования.  
  
 **Присоединить:** _PID_[**,**_PID_]  
 Начинает профилирование указанных процессов.  
  
 **Detach**[ **:** _PID_[,_PID_]]  
 Останавливает профилирование указанных процессов.  
  
## <a name="example"></a>Пример  
 В этом примере параметр **CrossSession** используется для присоединения к приложению, запущенному в другом консольном сеансе.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## <a name="see-also"></a>См. также:  
 [Средства](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)
