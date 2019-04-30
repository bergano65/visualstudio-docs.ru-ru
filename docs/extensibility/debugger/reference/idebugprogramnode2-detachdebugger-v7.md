---
title: IDebugProgramNode2::DetachDebugger_V7 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b7d97e277a3f7f327bf8830e49507d28e82568f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869843"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> РЕКОМЕНДУЕТСЯ К ИСПОЛЬЗОВАНИЮ. НЕ ИСПОЛЬЗУЙТЕ.

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

Этот метод вызывается, когда отладчик неожиданно завершает работу. При вызове этого метода, DE следует возобновить программы, как если бы, если пользователь отсоединены от него. Следует отправлять дальнейшие события отладки. Программа должна находиться в состоянии там, где это присоединяемого элемента из другой экземпляр отладчика.

## <a name="see-also"></a>См. также

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)