---
title: Перечисление БРЕАКРЕАСОН | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572621"
---
# <a name="breakreason-enumeration"></a>Перечисление BREAKREASON
Показывает, что вызвало прерывание.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
|BREAKREASON_STEP|Модуль языка находится в режиме пошагового выполнения.|  
|BREAKREASON_BREAKPOINT|Модуль языка обнаружил явную точку останова.|  
|BREAKREASON_DEBUGGER_BLOCK|Модуль языка обнаружил блок отладчика в другом потоке.|  
|BREAKREASON_HOST_INITIATED|Узел запросил разрыв.|  
|BREAKREASON_LANGUAGE_INITIATED|Обработчик языка запросил прерывание.|  
|BREAKREASON_DEBUGGER_HALT|Интегрированная среда разработки отладчика запросила прерывание.|  
|BREAKREASON_ERROR|Ошибка выполнения привела к разрыву.|  
|BREAKREASON_JIT|Вызвано запуском JIT-отладки.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)