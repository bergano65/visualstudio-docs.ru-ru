---
title: IDebugStopCompleteEvent2 | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719444"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Модуль отладки (DE) может отправить это необязательное событие в Диспетчер отладки сеансов (SDM) при остановке программы.

## <a name="syntax"></a>Синтаксис

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков

Этот интерфейс появился в Visual Studio 2005. Предыдущие выпуски не поддерживали асинхронную остановку.

- Метод " [останавливает](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) " вызывается SDM в многопроцессных или многопрограммных сценариях. Когда одна программа отправляет событие остановки в SDM, SDM запрашивает остановку других программ.

Остановить используется для асинхронного информирования SDM о том, что программа остановлена. Формирование модели SDM полезно для модуля отладки интерпретатора, где иногда нет кода, выполняемого в отлаживаемой программе, поэтому [не может быть](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) выполнено синхронно. Если модуль отладки хочет применить это асинхронное уведомление, он должен возвратить `S_ASYNC_STOP` из " [останавливается](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)".

## <a name="requirements"></a>Требования

Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
