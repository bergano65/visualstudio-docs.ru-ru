---
title: IDebugBeforeSymbolSearchEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d6f3f78e165ba2f4453131b7b459e3061243ff6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736112"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Движок отладки (DE) отправляет этот интерфейс диспетчеру отладки сеанса (SDM) для установки сообщения панели статуса во время нагрузок символов.

## <a name="syntax"></a>Синтаксис

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, когда он должен установить сообщение панели статуса во время нагрузок символа. Этот интерфейс реализован только путем отладки двигателей, которые работают с или являются частью скриптов переводчиков. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс (SDM использует **queryInterface** для доступа к интерфейсу **IDebugEvent2).**

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события, когда он должен установить сообщение панели статуса во время нагрузок символа. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при его подключении к отладке программы.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugBeforeSymbolSearchEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Извлекает имя модуля, который в настоящее время отлажен.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
