---
title: IDebugProgramNodeAttach2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721821"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Позволяет узлам программы получать уведомления о попытке присоединения к связанной программе.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован на том же классе, который реализует интерфейс [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для получения уведомления о операции присоединения и предоставления возможности отменить операцию присоединения.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Получите этот интерфейс, позвонив по методу `QueryInterface` в [объекте IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) Метод [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) должен быть вызван перед методом [присоединения,](../../../extensibility/debugger/reference/idebugengine2-attach.md) чтобы дать узлам программы шанс остановить процесс присоединения.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Прикрепляется к сопутствуеной программе или откладывает процесс присоединения к методу [присоединения.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Примечания
 Этот интерфейс является предпочтительной альтернативой унипраченному методу [Attach_V7.](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) Все отладочные двигатели `CoCreateInstance` всегда загружаются с функцией, то есть они мгновенно выходят за пределы отладки программы.

 Если предыдущая реализация `IDebugProgramNode2::Attach_V7` метода просто `GUID` устанавливала отладку программы, то необходимо реализовать только метод [OnAttach.](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

 Если предыдущая реализация `IDebugProgramNode2::Attach_V7` метода использовала предоставленный интерфейс обратного вызова, то эта функциональность должна быть `IDebugProgramNodeAttach2` перемещена в реализацию метода [Привязьки](../../../extensibility/debugger/reference/idebugengine2-attach.md) и интерфейс не должен быть реализован.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
