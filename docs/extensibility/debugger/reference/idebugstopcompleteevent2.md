---
title: IDebugStopCompleteEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719444"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Двигатель отладки (DE) может отправить это дополнительное событие менеджеру отладки сеанса (SDM) при прекращении программы.

## <a name="syntax"></a>Синтаксис

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей

Этот интерфейс был представлен Visual Studio 2005. Предыдущие релизы не поддерживали асинхронную остановку.

- [Остановка](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается SDM в многопроцессных или многопрограммных сценариях. Когда одна программа отправляет событие остановки в SDM, SDM просит другие программы, чтобы остановить, тоже.

Остановка используется для асинхронного информирования SDM о том, что программа остановлена. Информирование SDM полезно для движка отладки переводчика, где иногда внутри отладоченной программы не работает код, поэтому [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) не может быть завершена синхронно. Если отладка двигателя хочет использовать это асинхронное уведомление, он должен вернуться `S_ASYNC_STOP` из [Стоп](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).

## <a name="requirements"></a>Требования

Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
