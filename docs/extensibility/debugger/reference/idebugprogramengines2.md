---
title: IDebugProgramEngines2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b45cbe8cd1b68e1681b07fcdf1fc715973a11295
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325263"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Этот интерфейс используется узлами программы для указания всех возможных отладчики (DE), которые можно отлаживать этой программы.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE или пользовательский порт поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки установки определенных DE для конкретной программы.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProgramNode2` интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramEngines2`.

|Метод|Описание|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Указывает все возможные DEs, выполнять отладку этой программы.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Выбирает DE, используемые для отладки этой программы.|

## <a name="remarks"></a>Примечания
 После DE выбирается пользователем, этот выбор регистрируется с узлом программы путем вызова [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Выбранного ядра становится ядра, возвращенный [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)