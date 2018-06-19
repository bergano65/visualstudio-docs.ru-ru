---
title: IDebugStopCompleteEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed73821021d3a993507db9925c512119fbb98ca1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119254"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Модуль отладки (DE) может отправлять это необязательно событие диспетчера сеанса отладки (SDM), после остановки программы.

## <a name="syntax"></a>Синтаксис

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков

Этот интерфейс впервые появилась в Visual Studio 2005. Предыдущие выпуски не поддерживает асинхронной остановки.

[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается SDM в сценариях с несколькими процессами или несколькими программы. Когда одна программа отправляет событие остановки SDM, SDM запрашивает другие программы, чтобы остановить слишком.

Остановка используется для асинхронного информирования SDM, которая перестала программы. Информирования SDM полезен для интерпретатора ядра отладки, где иногда не выполняется код внутри отладки программы, это [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) не может выполняться синхронно. Если модуль отладки хочет использовать асинхронные уведомления, она должна вернуть `S_ASYNC_STOP` из [остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Требования

Заголовок: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll