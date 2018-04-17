---
title: IDebugExceptionEvent2::GetException | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: fc844885a7efa1784b985eb3901de80a47c5efe4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Возвращает подробное описание исключения, запустившем это событие.  
  
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
 [in, out] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуру, которая содержит описание исключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [C++] Вызывающий объект отвечает за освобождение всех строк в [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры, а также освобождение [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объекта в структуре.  
  
## <a name="see-also"></a>См. также  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)