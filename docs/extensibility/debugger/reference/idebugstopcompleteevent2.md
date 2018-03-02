---
title: "IDebugStopCompleteEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: aa8941decfb4e64906c57b719df711ce8779df9c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
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

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll