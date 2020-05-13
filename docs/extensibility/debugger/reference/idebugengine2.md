---
title: IDebugEngine2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730860"
---
# <a name="idebugengine2"></a>IDebugEngine2
Этот интерфейс представляет собой отладку двигателя (DE). Он используется для управления различными аспектами сеанса отладки, от создания точек разрыва до настройки и очистки исключений.

## <a name="syntax"></a>Синтаксис

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован на заказ DE для управления отладкой программ. Этот интерфейс должен быть реализован DE.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс вызывается менеджером отладки сеанса (SDM) для управления сеансом отладки, включая управление исключениями, создание моментов разрыва и реагирование на синхронные события, отправляемые DE.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngine2`.

|Метод|Описание|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Создает регистратор для всех программ, отладимых DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Прикрепляет DE к программе.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Создает отложенную точку разрыва в DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Определяет, как DE должен обрабатывать данное исключение.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Удаляет указанное исключение, чтобы оно больше не обрабатывалось движком отладки.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Удаляет список исключений, установленных IDE для определенной архитектуры или языка времени выполнения.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Получает GUID DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Информирует DE, что указанная программа была нетипично прекращена и что DE должен очистить все ссылки на программу и отправить событие уничтожения программы.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Вызванный SDM, чтобы указать, что синхронное событие отладки, ранее отправленное DE в SDM, было получено и обработано.|
|[Setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Устанавливает локал DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Устанавливает корень реестра, который в настоящее время используется DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Устанавливает метрику.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Запросы, чтобы все программы, отладимые этим DE, прекратили выполнение при следующей попытке выполнения одной из потоков.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
