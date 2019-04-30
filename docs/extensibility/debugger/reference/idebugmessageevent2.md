---
title: IDebugMessageEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49224ad0018286fffd365857364bf1b37300788f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918839"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Этот интерфейс используется ядром отладки (DE), чтобы отправить сообщение в Visual Studio, которая требует реакции от пользователя.

## <a name="syntax"></a>Синтаксис

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс для отправки сообщения в Visual Studio, которая требует ответ от пользователя. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейс должен быть реализован на один и тот же объект как следующий интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс.

 Реализация этого интерфейса должны взаимодействовать вызов Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) для DE. Например, это можно сделать с помощью сообщение, отправленное в обработку потока сообщений DE, или объект, реализующий этот интерфейс может содержать ссылку DE и обратный вызов DE с ответ, который передается в `IDebugMessageEvent2::SetResponse`.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 DE создает и отправляет этот объект события, для отображения сообщения пользователю, который требуется ответ. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функцию обратного вызова, предоставляемую SDM, когда он присоединен к отлаживаемой программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMessageEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Получает сообщение для отображения.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Задает ответ, если таковое имеется, из окна сообщения.|

## <a name="remarks"></a>Примечания
 DE будет использовать этот интерфейс, если он требует определенного ответа от пользователя для определенного сообщения. Например, если DE возвращает сообщение «Отказано в доступе» после попытки удаленно присоединиться к программе, DE отправляет этого конкретного сообщения в Visual Studio в `IDebugMessageEvent2` событие с тип окна сообщения `MB_RETRYCANCEL`. Это позволяет пользователю повторить или отменить операцию присоединения.

 DE указывает, как это сообщение будет обрабатываться, соответствующую соглашениям функции Win32 `MessageBox` (см. в разделе [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) сведения).

 Используйте [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) интерфейс для отправки сообщений в Visual Studio, которая не требует реакции от пользователя.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)