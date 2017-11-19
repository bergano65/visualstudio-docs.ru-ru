---
title: "Перечисление BREAKRESUMEACTION | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BREAKRESUMEACTION
apilocation: scrobj.dll
helpviewer_keywords: BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b830d314b1db40d7b83557d894ad6f8751bdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="breakresumeaction-enumeration"></a>Перечисление BREAKRESUMEACTION
Описывает способы продолжения выполнения из точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>Члены  
  
|Член|Описание|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|Прерывает приложение.|  
|BREAKRESUMEACTION_CONTINUE|Продолжает выполнение.|  
|BREAKRESUMEACTION_STEP_INTO|Выполняет шаг с заходом в процедуру.|  
|BREAKRESUMEACTION_STEP_OVER|Выполняет шаг с обходом процедуры.|  
|BREAKRESUMEACTION_STEP_OUT|Выходит из текущей процедуры.|  
|BREAKRESUMEACTION_IGNORE|Продолжает выполнение с состоянием.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|Переходит к следующему документу.|  
  
## <a name="see-also"></a>См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)