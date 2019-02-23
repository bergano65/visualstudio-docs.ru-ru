---
title: IEEDataStorage::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eff31ef70fc8cb812ff820a92653b6bb0cab6cd5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719500"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Возвращает число байтов, содержащихся в этом объекте.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

#### <a name="parameters"></a>Параметры
 `size`

 [out] Число байтов, содержащихся в этом объекте.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Используйте [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) метод для извлечения фактических данных байты.

## <a name="see-also"></a>См. также
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)