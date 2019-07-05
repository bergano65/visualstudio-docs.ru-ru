---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f363ba75d21b147eee6ad39276b949c703e932ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324461"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Извлекает идентификатор процесса, которому принадлежит объект, представленный этим [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) интерфейс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Параметры
`pProcID`\
[out] Идентификатор процесса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)