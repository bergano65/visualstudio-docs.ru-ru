---
title: IDebugMessageEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727363"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Этот интерфейс используется движком отладки (DE) для отправки сообщения в Visual Studio, которое требует ответа от пользователя.

## <a name="syntax"></a>Синтаксис

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы отправить сообщение в Visual Studio, которое требует ответа пользователя. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу.

 Реализация этого интерфейса должна сообщить visual Studio вызов [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) к DE. Например, это может быть сделано с сообщением, размещенным в потоке обработки сообщений DE, или объект, реализующий `IDebugMessageEvent2::SetResponse`этот интерфейс, может содержать ссылку на DE и перезвонить в DE с переданным ответом .

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект этого события для отображения сообщения пользователю, требующего ответа. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при подключении к отладочной программе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMessageEvent2`.

|Метод|Описание|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Отображает сяпотковое сообщение.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Устанавливает ответ, если таковое имеется, из окна сообщений.|

## <a name="remarks"></a>Примечания
 DE будет использовать этот интерфейс, если он требует конкретного ответа от пользователя для конкретного сообщения. Например, если DE получает сообщение "Отказ в доступе" после попытки удаленного присоединения к программе, `IDebugMessageEvent2` DE отправляет это `MB_RETRYCANCEL`конкретное сообщение в Visual Studio в случае со стилем коробки сообщений. Это позволяет пользователю повторить или отменить операцию присоединения.

 DE определяет, как это сообщение должно быть обработано, следуя конвенциям `MessageBox` функции Win32 (подробнее [см. AfxMessageBox).](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

 Используйте интерфейс [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) для отправки сообщений в Visual Studio, которые не требуют ответа от пользователя.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
