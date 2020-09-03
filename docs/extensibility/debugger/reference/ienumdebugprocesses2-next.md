---
title: 'IEnumDebugProcesses2:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbfab7f13160129249afe7139ef3c402ba9801ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715827"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
Возвращает следующий набор из перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProcess2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProcess2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>Параметры
`celt`\
[in] Количество получаемых элементов. Также указывает максимальный размер `rgelt` массива.

`rgelt`\
[вход, выход] Массив элементов [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , которые должны быть заполнены.

`pceltFetched`\
заполняет Возвращает количество элементов, фактически возвращаемых в `rgelt` .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если может быть возвращено меньше запрошенного числа элементов; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
