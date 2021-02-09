---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 843e5fdf91fe817681b95422474d3887de5756b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898612"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Не рекомендуется. НЕ ИСПОЛЬЗУЙТЕ.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Параметры

`pbstrHostMachineName`\
заполняет Возвращает имя компьютера, на котором выполняется программа.

## <a name="return-value"></a>Возвращаемое значение

Реализация всегда должна возвращать `E_NOTIMPL` .

## <a name="remarks"></a>Remarks

> [!WARNING]
> Начиная с Visual Studio 2005 этот метод больше не используется и всегда должен возвращать `E_NOTIMPL` .

## <a name="see-also"></a>См. также раздел

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
