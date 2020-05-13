---
title: IDebugEngine2::DэсстройПрограмма Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce139dd22361d9914693cbe8ad723656ab7d4f26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731108"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Информирует движок отладки (DE), что указанная программа была нетипично прекращена и что DE должен очистить все ссылки на программу и отправить событие уничтожения программы.

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

## <a name="parameters"></a>Параметры
`pProgram`\
(в) Объект [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) представляющий программу, которая была нетипично завершена.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 После вызова этого метода DE отправляет событие [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) обратно в диспетчер сессии отладки (SDM).

 Этот метод не реализуется (возвращается), `E_NOTIMPL`если DE выполняется в том же процессе, что и отладка программы. Этот метод реализуется только в том случае, если DE выполняется в том же процессе, что и SDM.

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
