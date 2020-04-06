---
title: IPropertyProxyEEside::CreateReplacementObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715039"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Создает копию объекта данных, специфичныя для оценщика выражения (EE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Параметры
`dataIn`\
(в) Объект [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) удерживая данные для копирования.

`dataOut`\
[out] Возвращает новый объект `IEEDataStorage`.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этому методу предоставляется объект [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) представляющий массив байтов. Этот входящий объект данных обычно не реализуется EE. Тем не менее, объект, возвращенный этим методом, всегда реализуется `IEEDataStorage` EE, что позволяет EE реализовать интерфейс на любом классе, который пожелает.

 Обратите внимание, что данные, предоставляемые входящим `IEEDataStorage` объектом, должны быть теми же данными в исходящих `IEEDataStorage` объектах.

## <a name="see-also"></a>См. также
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
