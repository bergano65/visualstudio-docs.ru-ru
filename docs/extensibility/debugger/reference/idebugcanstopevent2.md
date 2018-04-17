---
title: IDebugCanStopEvent2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 48f049648fcbd93d7ad7411a4dfeba8bbdb4431d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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