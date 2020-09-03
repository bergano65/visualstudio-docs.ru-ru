---
title: 'IEnumDebugPropertyInfo2:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d8e714f281835adf7df8d7e96a910ca66f1949b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715515"
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
Возвращает следующий набор из перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next(
   ULONG                 celt,
   DEBUG_PROPERTY_INFO** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   DEBUG_PROPERTY_INFO[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Количество получаемых элементов. Также указывает максимальный размер `rgelt` массива.

`rgelt`\
[вход, выход] Массив элементов [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , которые необходимо заполнить.

`pceltFetched`\
заполняет Возвращает количество элементов, фактически возвращаемых в `rgelt` .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если может быть возвращено меньше запрошенного числа элементов; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
