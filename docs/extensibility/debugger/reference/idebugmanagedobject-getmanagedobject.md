---
title: IDebugManagedObject::GetManagedObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a02fbe5b954fca78e2f75f982a62a1b9bf5f4a0b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210617"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Возвращает интерфейс, который представляет управляемый объект.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Параметры
`ppManagedObject`\
[out] Возвращает интерфейс, который представляет управляемый объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Можно запросить любой интерфейс, реализуемый управляемого класса, что позволяет вызывать его методы интерфейса, возвращаемый этим методом.

## <a name="see-also"></a>См. также
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)