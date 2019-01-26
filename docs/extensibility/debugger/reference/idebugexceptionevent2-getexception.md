---
title: IDebugExceptionEvent2::GetException | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6184a6283b6a93143132afdecb737f011794e96c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998174"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Возвращает подробное описание исключение, которое возникает это событие.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pExceptionInfo`  
 [in, out] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры, который заполняется описание исключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [C++] Вызывающий объект отвечает за освобождение все строки в [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры, а также освобождение [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объекта в структуре.  
  
## <a name="see-also"></a>См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)