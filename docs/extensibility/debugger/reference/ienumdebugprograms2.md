---
title: IEnumDebugПрограммы2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715570"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Этот интерфейс перечисляет программы, работающие в текущей сессии отладки.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы предоставить список программ, отладимых DE.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Visual Studio вызывает [EnumPrograms,](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) чтобы получить этот интерфейс. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) не используется Visual Studio.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPrograms2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Извлекает определенное количество программ в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Пропускает определенное количество программ в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Получает количество программ в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio использует этот интерфейс для:

- Заполнить окно **модулей** (позвонив [EnumPrograms,](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) а затем вызывая [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) по каждой программе).

- Заполните список присоединения `IDebugProcess2::EnumPrograms` к **процессу** (позвонив и позвонив в [queryInterface](/cpp/atl/queryinterface) на каждом интерфейсе [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) для получения интерфейса [IDebugEngineProgram2).](../../../extensibility/debugger/reference/idebugengineprogram2.md)

- Создайте список DEs, которые могут отладить каждую программу в процессе (с помощью [GetEngineInfo).](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)

- Применить Edit and Continue (ENC) обновления для каждой программы (позвонив IDebugProcess2::EnumPrograms, а затем вызова [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
