---
title: 'IDebugExceptionEvent2:: except | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a0e19dc924101fcceb93948272fc1e83353e2815
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163798"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает подробное описание исключения, которое вызвало это событие.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [вход, выход] Структура [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , которая заполняется описанием исключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 [Только C++] Вызывающий объект отвечает за освобождение всех строк в структуре [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , а также освобождение объекта [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) в структуре.  
  
## <a name="see-also"></a>См. также:  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
