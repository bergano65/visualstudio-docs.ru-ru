---
title: IDebugObject::УправляемыйDebugObject (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726693"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Создает копию управляемого объекта в адресном пространстве движка отладки.

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

## <a name="parameters"></a>Параметры
`ppObject`\
(ваут) Возвращает объект [IDebugManagedObject,](../../../extensibility/debugger/reference/idebugmanagedobject.md) представляющий вновь созданный управляемый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки. Возвращает E_FAIL, если этот [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) не представляет экземпляр управляемого класса значений.

## <a name="remarks"></a>Примечания
 Этот объект [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) должен представлять экземпляр управляемого `System.Decimal` класса значений, например экземпляр. Имея локальную копию, накладные расходы на вызов [Оценка](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) устраняется.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
