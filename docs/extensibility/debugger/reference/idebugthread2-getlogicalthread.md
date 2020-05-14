---
title: IDebugThread2::GetLogicalThread Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718836"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Двигатели Debug не реализуют этот метод.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Параметры
`pStackFrame`\
(в) Объект [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) представляющий кадр стека.

`ppLogicalThread`\
(ваут) Возвращает `IDebugLogicalThread2` интерфейс, представляющий связанный логический поток. Реализация отладоть двигатель должна установить это в нулевую величину.

## <a name="return-value"></a>Возвращаемое значение
 Внедрение движка debug всегда возвращается. `E_NOTIMPL`

## <a name="see-also"></a>См. также
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
