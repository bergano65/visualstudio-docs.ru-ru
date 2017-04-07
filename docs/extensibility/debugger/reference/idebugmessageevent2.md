---
title: "IDebugMessageEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: dfbe6b139a823fa13e9ce58284026c163cc07ffa
ms.lasthandoff: 04/05/2017

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
  
 DE определяет, как это сообщение может быть обработано соглашениям функцию Win32 `MessageBox` (см. [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) подробные сведения).  
  
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
