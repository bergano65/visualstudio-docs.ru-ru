---
title: IDebugCanStopEvent2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696672"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется для запроса диспетчера отладки сеанса (SDM) на то, следует ли останавливаться в текущем расположении кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для поддержки пошагового выполнения исходного кода. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс (модель SDM использует [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для доступа к `IDebugEvent2` интерфейсу).  
  
 Реализация этого интерфейса должна передавать вызов [КАНСТОП](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) SDM в модуль отладки. Например, это можно сделать с помощью сообщения, отправленного в поток обработки сообщений модуля отладки, или объекта, реализующего этот интерфейс, может содержать ссылку на модуль отладки и обратный вызов отладчика с флагом, переданным в `IDebugCanStopEvent2::CanStop` .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 DE может отправить этот метод каждый раз, когда запрос DE запрашивает продолжение выполнения, а DE — по пошаговому выполнению кода. Это событие отправляется с помощью функции обратного вызова [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , предоставляемой SDM при присоединении к отлаживаемой программе.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugCanStopEvent2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Возвращает причину этого события.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Указывает, должна ли отлаживаемая программа останавливаться в расположении этого события (и отправить событие, описывающее причину остановки) или просто продолжить выполнение.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Возвращает контекст документа, описывающий расположение этого события.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Возвращает контекст кода, описывающий расположение этого события.|  
  
## <a name="remarks"></a>Remarks  
 Параметр DE отправляет этот интерфейс, если пользователь выполняет шаги в функции, а параметр DE не находит отладочную информацию или отладочная информация существует, но параметр DE не знает, можно ли отобразить исходный код для этого расположения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
