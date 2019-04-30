---
title: IDebugObject::GetManagedDebugObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6738c70b75ff1e2f393b59e330ce57f2232de61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918532"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Создает копию управляемого объекта в адресном пространстве для обработчика отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

#### <a name="parameters"></a>Параметры
 `ppObject`

 [out] Возвращает [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объект, представляющий только что созданный управляемый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки. Возвращает значение E_FAIL, если данный [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) не представляет экземпляр класса управляемого значения.

## <a name="remarks"></a>Примечания
 Это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект должен представлять экземпляр класса управляемого значения, такие как `System.Decimal` экземпляра. Благодаря наличию локальную копию, затраты на вызов [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) исключается.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)