---
title: IDebugProgram2::GetProgramId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aba5ac3e17cb86219c065b5ed2372e127ad03dd2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320771"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Возвращает идентификатор GUID для этой программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Параметры
`pguidProgramId`\
[out] Возвращает `GUID` для этой программы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Отладчик (DE) должен возвращать идентификатор программы, которая изначально была передана [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) или [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) методы. Благодаря этому код программы в отладчике компонентов.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)