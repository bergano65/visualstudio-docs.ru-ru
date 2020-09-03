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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727696"
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
