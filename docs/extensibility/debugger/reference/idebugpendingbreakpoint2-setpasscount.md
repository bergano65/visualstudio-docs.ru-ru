---
title: IDebugPendingBreakpoint2::SetPassCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5af01702c20b4841c5d737bef2c3be7f885cc31e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340567"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Задает или изменяет число pass, связанные с ожидающая точка останова.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Параметры
`bpPassCount`\
[in] Объект [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуры, который содержит счетчик pass.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_BP_DELETED` Если точка останова была удалена.

## <a name="remarks"></a>Примечания
 Любой счетчик pass, который был ранее связан с ожидающая точка останова будет потеряно. Все точки останова, привязанный из этого ожидающих точек останова, называются присвоить их число pass `bpPassCount` параметра.

## <a name="see-also"></a>См. также
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)