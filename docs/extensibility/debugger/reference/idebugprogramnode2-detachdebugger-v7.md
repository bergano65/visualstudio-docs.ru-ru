---
title: IDebugProgramNode2::DetachDebugger-V7 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722106"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Устаревшие. НЕ ИСПОЛЬЗУЙТЕ.

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

Реализация должна всегда `E_NOTIMPL`возвращаться.

## <a name="remarks"></a>Примечания

> [!WARNING]
> По состоянию на Visual Studio 2005, этот `E_NOTIMPL`метод больше не используется и всегда должен вернуться .

Этот метод вызывается при неожиданном выходе отладчика. Когда этот метод вызывается, DE должен возобновить программу, как будто пользователь оторван от нее. Больше не следует отправлять события отладки. Программа должна находиться в состоянии, когда она может быть прикреплена из другого экземпляра отладчика.

## <a name="see-also"></a>См. также

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
