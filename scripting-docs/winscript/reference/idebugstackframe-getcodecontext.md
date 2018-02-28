---
title: "IDebugStackFrame::GetCodeContext | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugStackFrame.GetCodeContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetCodeContext
ms.assetid: 3dd378f3-e4b7-413e-8812-0f6c72952544
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b872e63169f6c2d70cd3476324b3d0071718350
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetcodecontext"></a>IDebugStackFrame::GetCodeContext
Возвращает текущий контекст кода, связанный с этим кадром стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetCodeContext(  
   IDebugCodeContext**  ppcc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppcc`  
 [out] Контекст кода, связанный с этим кадром стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает текущий контекст кода, связанный с этим кадром стека.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)