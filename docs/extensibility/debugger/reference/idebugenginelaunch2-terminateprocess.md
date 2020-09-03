---
title: 'IDebugEngineLaunch2:: Терминатепроцесс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::TerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::TerminateProcess
ms.assetid: f7039e7f-5f57-4222-9ad2-11a66b2da6e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 971259edc89d1ad8be01b6e6e4db46f760534349
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730510"
---
# <a name="idebugenginelaunch2terminateprocess"></a>IDebugEngineLaunch2::TerminateProcess
Завершает процесс.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT TerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int TerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Параметры
`pProcess`\
окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, который должен быть завершен.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Перед вызовом этого метода вызовите метод [кантерминатепроцесс](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)
