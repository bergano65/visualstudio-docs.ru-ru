---
title: BP_LOCATION_DATA_STRING | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d2ac74699593818b2a84ae767278189cfd195195
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243208"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Используется для задания точки останова по данным, которые основаны на строку, пользователь может ввести в интегрированной среде разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Участники  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в который происходит точки останова.  
  
 `bstrContext`  
 Контекст точки останова в коде, обычно имя метода или функции материал в стеке вызовов.  
  
 `bstrDataExpr`  
 Строка данных пользователь вводит задается точка останова.  
  
 `dwNumElements`  
 Число элементов в строке данных, в котором происходит точки останова.  
  
## <a name="remarks"></a>Примечания  
 Эта структура является членом [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру как часть объединения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

