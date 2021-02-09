---
title: 'Иенумдебугаддрессес:: NOCOUNT | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4a2d6fab85b392a517cc8275462bd8a01bb4316
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923073"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
Этот метод возвращает количество элементов в перечислении.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Параметры
`pcelt`\
заполняет Возвращает количество элементов в перечислении.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод не является частью пользовательского интерфейса перечисления COM, который указывает, что необходимо реализовать только следующие методы: "только следующий", "клонировать", "пропустить" и "Сброс".

## <a name="see-also"></a>См. также раздел
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
