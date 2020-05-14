---
title: IEnumDebugCustomАтрибуты::Следующий Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08228fe4a630eac37c38f4eb247dc91678d8e2e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717231"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
Извлекает определенное количество пользовательских атрибутов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Количество получаемых элементов. Также указывается максимальный размер `rgelt` массива.

`rgelt`\
(ваут) Массив объектов [IDebugCustomAttribute,](../../../extensibility/debugger/reference/idebugcustomattribute.md) которые должны быть заполнены.

`pceltFetched`\
(ваут) Возвращает количество элементов, `rgelt`фактически возвращенных в .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает, `S_FALSE` если меньше, чем просили количество элементов может быть возвращено; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
