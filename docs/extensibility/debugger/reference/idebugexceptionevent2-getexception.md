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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8fad5aca8dcb548718c6acabb5c58e8c31592558
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950807"
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