---
title: IDebugCanStopEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734509"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Этот интерфейс используется для того, чтобы спросить менеджера отладки сеанса (SDM), стоит ли останавливаться на текущем местоположении кода.

## <a name="syntax"></a>Синтаксис

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс для поддержки шага через исходный код. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот `IDebugEvent2` интерфейс (SDM использует [queryInterface](/cpp/atl/queryinterface) для доступа к интерфейсу).

 Реализация этого интерфейса должна сообщить вызов SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) к движку отладки. Например, это можно сделать с помощью сообщения, размещенного на потоке обработки сообщений отладки, или объект, реализующий этот `IDebugCanStopEvent2::CanStop`интерфейс, может содержать ссылку на движок отладки и перезвонить обратно в движок отладки с переданным флагом.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE может отправлять этот метод каждый раз, когда DE просят продолжить выполнение и DE шагает через код. Это событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при его подключении к отладке программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugCanStopEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Получает причину этого события.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Определяется, должна ли отладить программу останавливаться в месте расположения этого события (и отправлять событие, описывающие причину остановки) или просто продолжать выполнение.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Получает контекст документа, описывающий местоположение этого события.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Получает контекст кода, описывающий местоположение этого события.|

## <a name="remarks"></a>Примечания
 DE отправляет этот интерфейс, если пользователь вступает в функцию и DE не находит информацию об отладке там или информация об отладке существует, но DE не знает, если исходный код может быть отображено для этого местоположения.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
