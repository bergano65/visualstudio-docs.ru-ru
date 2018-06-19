---
title: IDebugMessageEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d0cb1f270d3d3ae77c43ea89fba5b7483e80412
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116179"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Этот интерфейс используется подсистема отладки (DE) для отправки сообщения в Visual Studio, который требует ответа от пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для отправки сообщения в Visual Studio, который требует ответа пользователя. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс. Использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейса.  
  
 Реализация этого интерфейса должны взаимодействовать вызов Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) значение DE. Например, это можно сделать с сообщением, опубликованных для обработки потока сообщений DE, или объект, реализующий этот интерфейс может содержать ссылку DE и обратный вызов DE с ответом, переданные в `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE создает и отправляет этот объект события для отображения сообщения пользователю, который требует ответа. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемую SDM, когда он присоединяется к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugMessageEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Возвращает сообщение для отображения.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Задает ответ, если таковая имеется, из окна сообщения.|  
  
## <a name="remarks"></a>Примечания  
 DE будет использовать этот интерфейс, если он требует определенного ответа от пользователя для конкретного сообщения. Например, если DE возвращает сообщение «Доступ запрещен» после попытки удаленно присоединения к программе, DE отправляет это конкретное сообщение в Visual Studio в `IDebugMessageEvent2` событие с тип окна сообщения `MB_RETRYCANCEL`. Это позволяет пользователю повторить попытку или отменить операцию присоединения.  
  
 DE определяет, как это сообщение может быть обработано соглашениям функцию Win32 `MessageBox` (см. [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) подробные сведения).  
  
 Используйте [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) интерфейс для отправки сообщений в Visual Studio, не требующие ответа от пользователя.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)