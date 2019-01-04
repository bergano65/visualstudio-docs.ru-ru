---
title: IDebugStopCompleteEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39da50c17d4d4b8b02390e0d2960d5696b93b1f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932901"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Модуль отладки (DE) можно отправлять это необязательное событие диспетчер отладки сеансов (SDM) после остановки программы.

## <a name="syntax"></a>Синтаксис

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков

Этот интерфейс впервые появилась в Visual Studio 2005. Предыдущие версии не поддерживает асинхронной остановки.

[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается SDM в сценариях с несколькими процессами или несколькими программы. Если для одной из них отправляет событие stopping SDM, SDM запрашивает другие программы, чтобы остановить, слишком.

Остановка используется для асинхронного информирования SDM, который перестал программы. О том, SDM полезно для отладки двигателя интерпретатор, котором иногда не выполняется код внутри отладки программы, это [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) не может быть завершена синхронно. Если модуль отладки хочет использовать этот асинхронное уведомление, оно должно возвращать `S_ASYNC_STOP` из [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Требования

Заголовок: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll