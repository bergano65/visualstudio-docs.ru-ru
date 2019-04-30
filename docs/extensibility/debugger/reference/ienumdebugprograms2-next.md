---
title: IEnumDebugPrograms2::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96f46692b86f35c999e21541b9c8c7a7dcc7f670
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866048"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
Возвращает следующий набор элементов из перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProgram2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProgram2[] rgelt,
   ref uint         pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 `celt`

 [in] Количество извлекаемых элементов. Также указывает максимальный размер `rgelt` массива.

 `rgelt`

 [in, out] Массив [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) элементов для заполнения.

 `pceltFetched`

 [out] Возвращает количество элементов, фактически возвращенных в `rgelt`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше, чем запрошенное количество элементов может быть возвращено; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)