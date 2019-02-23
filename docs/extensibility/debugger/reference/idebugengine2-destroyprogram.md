---
title: IDebugEngine2::DestroyProgram | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f626005621604d367f5878e36899aa2ff46114ee
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678453"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Информирует модуля отладки (DE), то программа, указанная операция была прервана необычайно и что DE следует удалить все ссылки на программы и события уничтожения отправки программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DestroyProgram( 
   IDebugProgram2* pProgram
);
```

```cpp
int DestroyProgram( 
   IDebugProgram2 pProgram
);
```

#### <a name="parameters"></a>Параметры
 `pProgram`

 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, которая необычайно был завершен.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 После вызова этого метода, DE отправляет [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) событие диспетчер отладки сеансов (SDM).

 Этот метод не реализован (возвращает `E_NOTIMPL`) Если DE выполняется в том же процессе, что отлаживаемой программы. Этот метод реализуется только в том случае, если DE выполняется в том же процессе, что SDM.

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)