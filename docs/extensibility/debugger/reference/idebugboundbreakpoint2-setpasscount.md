---
title: IDebugBoundBreakpoint2:SetPassCount (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735433"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Устанавливает или изменяет количество пропусков, связанное с этой связанной точкой разрыва.

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
(в) Структура [BP_PASSCOUNT,](../../../extensibility/debugger/reference/bp-passcount.md) которая определяет количество проходов.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращается, `E_BP_DELETED` если состояние объекта точки разрыва `BPS_DELETED` установлено (часть [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) перечисления).

## <a name="remarks"></a>Примечания
 Подсчет проходов определяет, когда точка разрыва высвобовывается. Текущий пропуск или количество попаданий можно получить, позвонив по методу [GetHitCount.](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)

 Любой проходный счет, который ранее был связан с этой точкой разрыва, теряется.

## <a name="see-also"></a>См. также
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
