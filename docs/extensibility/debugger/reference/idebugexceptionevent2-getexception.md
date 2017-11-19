---
title: "IDebugExceptionEvent2::GetException | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::GetException
helpviewer_keywords: IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cc68f7fb843e97e9333aa8d0223ed601df98273
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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