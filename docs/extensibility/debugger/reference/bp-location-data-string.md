---
title: "BP_LOCATION_DATA_STRING | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_DATA_STRING
helpviewer_keywords: BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7952392b55f351332ba8163fe1bd4c04c3883d87
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Используется для задания точки останова в данных, основанных на строку, пользователь может ввести из интегрированной среды разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Члены  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в который происходит точки останова.  
  
 `bstrContext`  
 Контекст точки останова в коде, обычно имя метода или функции по результатам в стеке вызова.  
  
 `bstrDataExpr`  
 Строка данных пользователь вводит задается точка останова.  
  
 `dwNumElements`  
 Количество элементов в строке данных, в котором происходит точки останова.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)