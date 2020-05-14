---
title: IEEDataStorage::GetData Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718210"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Извлекает указанное количество байтов с объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Параметры
`dataSize`\
(в) Количество байтов для извлечения `data` (массив должен содержать хотя бы это количество байтов).

`sizeGotten`\
(ваут) Возвращает количество байтов, фактически извлеченных.

`data`\
(в, вне) Массив, который должен быть заполнен запрошенными данными.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Рекомендуемое использование этого метода заключается в том, чтобы получить все байты данных в локальный массив, так как нет никакого способа, чтобы пропустить байты в процессе поиска. В этом случае `dataSize` параметр должен быть значением, возвращенным методом [GetSize.](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

## <a name="see-also"></a>См. также
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
