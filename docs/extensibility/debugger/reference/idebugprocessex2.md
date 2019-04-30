---
title: IDebugProcessEx2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0b29d88387ccb2ed711f1a000bf7bb00a34dd01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870701"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Этот интерфейс позволяет сеанс отладки manager (SDM) рассылать уведомления процесса, присоединение или отсоединение от процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский порт поставщик реализует этот интерфейс на один и тот же объект как [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, в следующем порядке:

- Отслеживание поддержки сеансы, подключенные к процессу

- Поддержка автоматического присоединения через несколько отладчиков

  Если он выбирает поставщика пользовательского порта можно реализовать этот интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов

- Вызовы SDM [QueryInterface](/cpp/atl/queryinterface) на `IDebugProcess2` интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessEx2`.

|Метод|Описание|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Информирует процесса о том, что сеанс теперь является отладка процесса.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Информирует процесса о том, что сеанс больше не является отладка процесса.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Добавляет узлы программы список обработчиков отладки.|

## <a name="remarks"></a>Примечания
 Этот интерфейс является закрытым между SDM и процессом.

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)