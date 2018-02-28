---
title: "Перечисление BREAKREASON | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="breakreason-enumeration"></a>Перечисление BREAKREASON
Показывает, что вызвало прерывание.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|BREAKREASON_STEP|Обработчик языка находится в пошаговом режиме.|  
|BREAKREASON_BREAKPOINT|Обработчик языка обнаружил явная точка останова.|  
|BREAKREASON_DEBUGGER_BLOCK|Обработчик языка обнаружил блок отладчика в другом потоке.|  
|BREAKREASON_HOST_INITIATED|Узел запросил разрыв.|  
|BREAKREASON_LANGUAGE_INITIATED|Обработчик языка запросил разрыв.|  
|BREAKREASON_DEBUGGER_HALT|Разрыв запрошенной отладчиком интегрированной среды разработки.|  
|BREAKREASON_ERROR|Ошибка выполнения вызвало прерывание.|  
|BREAKREASON_JIT|Причина запуска JIT-отладка.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)