---
title: IPropertyProxyEeside:InPlaceUpdateObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714892"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Обновляет данные объекта с данным объектом данных и возвращает новый объект данных, представляющий новые данные объекта.

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

## <a name="parameters"></a>Параметры
`dataIn`\
(в) Объект [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) содержащий новые данные.

`dataOut`\
(ваут) Возвращает новый `IEEDataStorage` объект, содержащий заменяемые данные.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод фактически обновляет данные объекта. Данные в возвращенном объекте [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) не должны быть такими `IEEDataStorage` же, как данные в входящий объект, но возвращенный объект должен отражать текущее значение объекта.

 Входящие объекты данных, как правило, не реализуются EE. Тем не менее, объект, возвращенный этим методом, всегда реализуется `IEEDataStorage` EE, что позволяет EE реализовать интерфейс на любом классе, который пожелает.

 Метод [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) создает объект данных на основе входящего объекта данных, но не влияет на исходные данные объекта.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
