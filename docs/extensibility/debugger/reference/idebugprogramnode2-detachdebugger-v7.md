---
title: IDebugProgramNode2::D etachDebugger_V7 | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722106"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ.

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

Реализация всегда должна возвращать `E_NOTIMPL` .

## <a name="remarks"></a>Remarks

> [!WARNING]
> Начиная с Visual Studio 2005 этот метод больше не используется и всегда должен возвращать `E_NOTIMPL` .

Этот метод вызывается при внезапном завершении работы отладчика. При вызове этого метода программа DE должна возобновить работу программы так, как будто пользователь отсоединяется от нее. Больше не нужно отправлять события отладки. Программа должна находиться в состоянии, в котором она может быть присоединена из другого экземпляра отладчика.

## <a name="see-also"></a>См. также раздел

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
