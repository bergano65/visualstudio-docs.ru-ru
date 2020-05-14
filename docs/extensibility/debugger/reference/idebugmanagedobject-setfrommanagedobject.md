---
title: IDebugManagedObject::SetFromManagedObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727696"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Устанавливает значение экземпляра объекта класса значений из экземпляра класса значений, предусмотренного в качестве параметра.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Параметры
`pManagedObject`\
(в) Интерфейс, представляющий управляемый объект, содержащий новое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод используется для изменения управляемого объекта в представлении объекта [IDebugManagedObject.](../../../extensibility/debugger/reference/idebugmanagedobject.md)

## <a name="see-also"></a>См. также
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
