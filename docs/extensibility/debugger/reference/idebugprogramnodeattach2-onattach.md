---
title: IDebugProgramNodeAttach2::OnAttach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79f15102b5adae2112f4abdeeb68b80962895e8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916803"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Присоединяется к соответствующую программу или откладывает процесс присоединения к [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

#### <a name="parameters"></a>Параметры
 `guidProgramId`

 [in] `GUID` Чтобы назначить соответствующую программу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) не следует вызывать метод. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод вызывается во время присоединения, прежде чем [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод. `OnAttach` Метод может выполнить сам процесс attach (в этом случае этот метод возвращает `S_FALSE`) или отложить процесс присоединения к `IDebugEngine2::Attach` метод ( `OnAttach` возвращает метод `S_OK`). В любом случае `OnAttach` можно задать метод `GUID` программы, отлаживаемой в данный `GUID`.

## <a name="see-also"></a>См. также
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)