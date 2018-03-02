---
title: "IDebugProgramNode2::DetachDebugger_V7 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fdf4875c30bebaeed925af57c0d80910f8fcbf21
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
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