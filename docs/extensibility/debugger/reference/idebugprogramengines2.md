---
title: IDebugProgramEngines2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722401"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Этот интерфейс используется узлами программы для определения всех возможных отладок двигателей (DE), которые могут отладить эту программу.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE или поставщик пользовательских портов реализует этот интерфейс на том же объекте, который реализует [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки создания конкретного DE для использования для конкретной программы.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [queryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` на интерфейс, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgramEngines2`.

|Метод|Описание|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Указывает все возможные DEs, которые могут отладить эту программу.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Выбирает DE для использования для отладки этой программы.|

## <a name="remarks"></a>Примечания
 Как только DE выбран пользователем, этот выбор регистрируется в узлах программы, позвонив [в SetEngine.](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md) Выбранный двигатель становится двигателем, возвращенным [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
