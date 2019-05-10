---
title: IEnumDebugObjects::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92fdfe08855fb9e70d24652e4361d9fe521209a2
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225546"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Этот метод возвращает следующий набор элементов из перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next(
   ULONG          celt,
   IDebugObject** rgelt,
   ULONG*         pceltFetched
);
```

```csharp
int Next(
   uint           celt,
   IDebugObject[] rgelt,
   ref uint       pceltFetched
);
```

## <a name="parameters"></a>Параметры
 `celt`\

 [in] Количество извлекаемых элементов. Также указывает максимальный размер `rgelt` массива.

 `rgelt`\

 [in, out] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) элементов для заполнения.

 `pceltFetched`\

 [out] Возвращает количество элементов, фактически возвращенных в `rgelt`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше, чем запрошенное количество элементов может быть возвращено; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)