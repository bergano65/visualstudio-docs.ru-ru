---
title: IDebugCanStopEvent2 | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: c5313595bd96b2176255822425d11776eedaedbe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942246"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Этот интерфейс используется для запроса диспетчер отладки сеансов (SDM), следует ли остановить от текущей позиции кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для поддержки пошагового выполнения исходного кода. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).  
  
 Реализация этого интерфейса должны взаимодействовать вызов SDM [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) к модулю отладки. Например, это можно сделать с помощью сообщение, отправленное в обработку потока сообщений обработчика отладки или объект, реализующий этот интерфейс может содержать ссылку на модуль отладки и обратный вызов обработчика отладки с флагом, передаваемые в `IDebugCanStopEvent2::CanStop`.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот метод каждый раз, когда будет предложено продолжить выполнение и DE DE пошаговое выполнение кода может отправлять DE. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, если он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCanStopEvent2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Возвращает причину для данного события.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Указывает, следует остановиться на расположение этого события (и отправить событие, описывающее причину остановки) или просто продолжить выполнение отлаживаемой программы.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Получает контекст документа, который описывает расположение этого события.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Возвращает контекст кода, которое описывает расположение этого события.|  
  
## <a name="remarks"></a>Примечания  
 DE отправляет этот интерфейс, если действия пользователя в функцию и DE находит сведения об отладке существует или существует отладочной информации, но также DE не знает, если исходный код можно отображать для этого расположения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)