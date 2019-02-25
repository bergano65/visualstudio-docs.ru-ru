---
title: IPropertyProxyEESide::InPlaceUpdateObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8617dd6f37d7e90d23c3ed454ef56122b36f6b75
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688645"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Обновляет данные объекта с данным объектом и возвращает новый объект данных, предоставляющий новые данные объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

#### <a name="parameters"></a>Параметры
 `dataIn`

 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий новые данные.

 `dataOut`

 [out] Возвращает новый `IEEDataStorage` объект, содержащий замененными данными.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Фактически, этот метод обновляет данные объекта. Данные в возвращаемом [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект не должен быть таким же, как данные во входящем `IEEDataStorage` объект, но возвращаемый объект должен отражать текущее значение свойства.

 Входящий объект данных обычно не реализуют EE. Тем не менее, объект, возвращаемый этим методом всегда реализуется EE, которая позволяет реализовать EE `IEEDataStorage` интерфейс требуется любой класс.

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) метод создает объект данных, на основе входящего объекта данных, но не влияет на свойства исходных данных.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)