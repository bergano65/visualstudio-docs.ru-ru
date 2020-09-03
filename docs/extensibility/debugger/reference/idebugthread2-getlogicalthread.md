---
title: 'IDebugThread2:: Жетлогикалсреад | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718836"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Отладчики не реализуют этот метод.

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
окне Объект [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , представляющий кадр стека.

`ppLogicalThread`\
заполняет Возвращает `IDebugLogicalThread2` интерфейс, представляющий связанный логический поток. Реализация модуля отладки должна установить значение null.

## <a name="return-value"></a>Возвращаемое значение
 Реализации модуля отладки всегда возвращают `E_NOTIMPL` .

## <a name="see-also"></a>См. также раздел
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
