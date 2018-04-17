---
title: IDebugProgramNode2::DetachDebugger_V7 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a79c073048fe30a4abed069487ad09943253475
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ СЛЕДУЕТ ИСПОЛЬЗОВАТЬ.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Возвращаемое значение

Реализация всегда должны возвращать `E_NOTIMPL`.

## <a name="remarks"></a>Примечания

> [!WARNING]
> Начиная с Visual Studio 2005, этот метод больше не используется и всегда должны возвращать `E_NOTIMPL`.

Этот метод вызывается, когда отладчик аварийно завершает работу. При вызове этого метода DE должен продолжить программу так, будто пользователь отсоединяется от него. Нет дополнительные события отладки, необходимо отправить. Программа должна находиться в состоянии там, где это присоединяемого из другого экземпляра отладчика.

## <a name="see-also"></a>См. также

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)