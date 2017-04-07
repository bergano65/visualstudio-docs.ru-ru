---
title: "IDebugCanStopEvent2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
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
ms.openlocfilehash: 00cfe8409762119c15cbe188b1a20b7a6466ea4a
ms.lasthandoff: 04/05/2017

---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Этот интерфейс используется для попросите диспетчера сеанса отладки (SDM), следует ли остановить по текущему пути кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для поддержки пошагового выполнения исходного кода. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).  
  
 Реализация этого интерфейса должны взаимодействовать SDM вызов [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) для модуля отладки. Например, это можно сделать с сообщением, опубликованных для обработки потока сообщений модуль отладки или объект, реализующий этот интерфейс может содержать ссылку на модуль отладки и обратный вызов модуль отладки с помощью флага, переданные в `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот метод каждый раз, когда будет предложено продолжить выполнение "и" DE "DE пошаговое выполнение кода может отправлять DE. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, когда он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCanStopEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Возвращает причину для данного события.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Указывает, следует остановиться на расположение этого события (и отправить событие, которое описывает причину остановки) или просто продолжить выполнение отлаживаемой программы.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Возвращает контекст документ, описывающий расположение этого события.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Возвращает контекст кода, которое описывает расположение этого события.|  
  
## <a name="remarks"></a>Примечания  
 DE отправляет этот интерфейс, если действия пользователя в функцию и DE находит сведения об отладке существует или существует отладочной информации, но DE не знает, если исходный код могут отображаться для этого расположения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
