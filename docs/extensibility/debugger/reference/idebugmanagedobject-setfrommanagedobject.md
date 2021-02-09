---
title: 'Идебугманажедобжект:: Сетфромманажедобжект | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c1f18fbfa70faf1d3da8ae785768419765dc94b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890231"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Задает значение экземпляра объекта класса значения из экземпляра класса значений, указанного в качестве параметра.

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
окне Интерфейс, представляющий управляемый объект, содержащий новое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод используется для изменения управляемого объекта, представленного объектом [идебугманажедобжект](../../../extensibility/debugger/reference/idebugmanagedobject.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
