---
title: IDebugEngineLaunch2::CanTerminateProcess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d8f401ae49edb2f77d35104de68280be322a63d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337221"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Определяет, может быть завершен процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Параметры
`pProcess`\
[in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий к завершению процесса.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_FALSE` Если ядро невозможно завершить процесс, к примеру, так как отказано в доступе.

## <a name="remarks"></a>Примечания
 Если этот метод возвращает `S_OK`, затем его [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) метод может вызываться действительности завершить процесс.

## <a name="see-also"></a>См. также
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)