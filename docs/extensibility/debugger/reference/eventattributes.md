---
title: "EVENTATTRIBUTES | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVENTATTRIBUTES
helpviewer_keywords: EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097a61ff6c96fd4901265ad960169fd5ec7244c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
Задает атрибуты события.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
typedef DWORD EVENTATTRIBUTES;  
```  
  
```csharp  
public enum enum_EVENTATTRIBUTES {   
   EVENT_ASYNCHRONOUS          = 0x0000,  
   EVENT_SYNCHRONOUS           = 0x0001,  
   EVENT_STOPPING              = 0x0002,  
   EVENT_ASYNC_STOP            = 0x0002,  
   EVENT_SYNC_STOP             = 0x0003,  
   EVENT_IMMEDIATE             = 0x0004,  
   EVENT_EXPRESSION_EVALUATION = 0x0008  
};  
```  
  
## <a name="members"></a>Члены  
 EVENT_ASYNCHRONOUS  
 Указывает, что событие является асинхронным и необходимости ответ на событие.  
  
 EVENT_SYNCHRONOUS  
 Указывает, что событие является синхронным; ответ с помощью параметра [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md).  
  
 EVENT_STOPPING  
 Указывает, что это событие остановки. Должны быть объединены с помощью `EVENT_ASYNCHRONOUS` или `EVENT_SYNCHRONOUS`.  
  
 EVENT_ASYNC_STOP  
 Обозначает событие остановки асинхронной. В настоящее время нет такого события. Этот флаг доступен только заполнителем.  
  
 EVENT_SYNC_STOP  
 Указывает на событие синхронной остановки (сочетание `EVENT_SYNCHRONOUS` и `EVENT_STOPPING`). Это значение используется модулем отладки (DE) при отправке события остановки. Ответ осуществляется посредством вызова [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md), или [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
 EVENT_IMMEDIATE  
 Указывает событие, которое отправляется немедленно и синхронно в интегрированную среду разработки. Этот флаг используется в сочетании с другими флагами как `EVENT_ASYNCHRONOUS`, `EVENT_SYNCHRONOUS`, или `EVENT_SYNC_STOP` для указания типа события и тот факт, что известен механизм ответа (если таковые имеются).  
  
 EVENT_EXPRESSION_EVALUATION  
 Это событие является результатом вычисления выражения.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются в `dwAttrib` параметр [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод.  
  
 Эти значения могут объединяться с помощью битового оператора `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)