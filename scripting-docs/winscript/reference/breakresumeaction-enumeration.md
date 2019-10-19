---
title: Перечисление BREAKRESUMEACTION | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572610"
---
# <a name="breakresumeaction-enumeration"></a>Перечисление BREAKRESUMEACTION
Описывает способы продолжения выполнения из точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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