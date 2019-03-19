---
title: Перечисление BREAKREASON | Документация Майкрософт
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
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160593"
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
  
## <a name="members"></a>Участники  
  
|Член|Описание:|  
|------------|-----------------|  
|BREAKREASON_STEP|Модуль языка находится в пошаговом режиме.|  
|BREAKREASON_BREAKPOINT|Модуль языка произошла явная точка останова.|  
|BREAKREASON_DEBUGGER_BLOCK|Модуль языка обнаружил блок отладчика в другом потоке.|  
|BREAKREASON_HOST_INITIATED|Узел запрошенные разрыв.|  
|BREAKREASON_LANGUAGE_INITIATED|Модуль языка запрошенные разрыв.|  
|BREAKREASON_DEBUGGER_HALT|Разрыв запрошенной отладчиком интегрированной среды разработки.|  
|BREAKREASON_ERROR|Ошибка выполнения вызвало прерывание.|  
|BREAKREASON_JIT|Из-за запуска, JIT-отладка.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)