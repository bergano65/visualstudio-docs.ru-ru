---
title: IDebugEngine2::RemoveAllSetExceptions | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c870c158a0ad3bcd0769c9bf9c0e0e4595a9c9f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873808"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Удаляет из списка исключений, заданные в интегрированной среде разработки для конкретной архитектуры среды выполнения или языка.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidType`  
 [in] Идентификатор GUID для языка, или идентификатор GUID для обработчика отладки, предназначенную для архитектуры среды выполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Удалены с помощью данного метода исключения установленные с предыдущими вызовами к [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) метод.  
  
 Чтобы удалить определенное исключение, вызовите [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)