---
title: IDebugProgramNodeAttach2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 255d057154b9814cb81325a737324c18de470bc8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717056"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Позволяет узлу программы для получения уведомлений об попытка присоединить соответствующую программу.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется для одного класса, реализующего [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) интерфейс, чтобы получать уведомления об операции присоединения и предоставляют возможность отменить операцию присоединения.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Получить этот интерфейс, вызвав `QueryInterface` метод в [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекта. [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен вызываться перед [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод, чтобы предоставить возможность остановить этот процесс на узле программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Присоединяется к соответствующую программу или откладывает процесс присоединения к [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.|

## <a name="remarks"></a>Примечания
 Этот интерфейс является предпочтительным вариантом для устаревших [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) метод. Все модули отладки, всегда загружаются с `CoCreateInstance` функции, то есть они создаются вне адресного пространства отлаживаемой программы.

 Если предыдущей реализации `IDebugProgramNode2::Attach_V7` метод просто устанавливает `GUID` из отлаживаемой программы, затем только [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен быть реализован.

 Если предыдущей реализации `IDebugProgramNode2::Attach_V7` метод, используемый интерфейс обратного вызова, который был предоставлен, то эта функциональность должна переместиться на реализацию [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод и `IDebugProgramNodeAttach2` не поддерживает интерфейс должен быть реализован.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)