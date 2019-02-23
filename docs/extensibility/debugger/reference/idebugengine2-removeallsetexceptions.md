---
title: IDebugEngine2::RemoveAllSetExceptions | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f5eb2542fa16d86dd342ae0e2783ac03ca69ee4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703413"
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
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)