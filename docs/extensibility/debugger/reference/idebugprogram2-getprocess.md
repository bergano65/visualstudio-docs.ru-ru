---
title: IDebugProgram2::GetProcess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b307fb7b4a25fc5a84b30eefd65e72b4f387a07d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313767"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Получение, на котором выполняется эта программа, в процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Параметры
`ppProcess`\
[out] Возвращает [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, представляющий процесс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если отладчик (DE) реализует [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) интерфейс, DE реализация этого метода всегда должны возвращать `E_NOTIMPL` поскольку DE не может определить, какой процесс, он выполняется в и, следовательно, не может удовлетворять реализация этого метода.

 Реализация `IDebugEngineLaunch2` интерфейс означает, что DE необходимо знать, как создать процесс; таким образом, DE реализация [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) могут узнать, какой процесс выполняется в интерфейс.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)