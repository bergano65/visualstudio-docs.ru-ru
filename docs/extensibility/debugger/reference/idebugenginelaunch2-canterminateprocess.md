---
title: 'IDebugEngineLaunch2:: Кантерминатепроцесс | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91c68e0a0e314015c1f2e6df2a96243c6ce854e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730556"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Определяет, можно ли завершить процесс.

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
окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, который должен быть завершен.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает `S_FALSE` , если обработчик не может завершить процесс, например из-за отказа в доступе.

## <a name="remarks"></a>Remarks
 Если этот метод возвращает значение `S_OK` , то для фактического завершения процесса можно вызвать метод [терминатепроцесс](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
