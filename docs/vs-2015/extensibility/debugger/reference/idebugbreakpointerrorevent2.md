---
title: IDebugBreakpointErrorEvent2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 341f65c1a7e441c81e91fca5a66dd302a30849d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730953"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс указывает диспетчер отладки сеансов (SDM), ожидающая точка останова не были привязаны в загрузить программу, из-за предупреждение или ошибку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс как часть поддержки точек останова. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для доступа к `IDebugEvent2` интерфейс).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 DE создает и отправляет этот объект события в том случае, если ожидающая точка останова не может быть привязано к отлаживаемой программы. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, если он присоединен к отлаживаемой программы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBreakpointErrorEvent2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Получает [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейс, который описывает предупреждения или ошибки.|  
  
## <a name="remarks"></a>Примечания  
 Каждый раз, когда привязана точка останова, событие передается SDM. Если точка останова не может быть привязана, `IDebugBreakpointErrorEvent2` передаются; в противном случае — значение [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) отправляется.  
  
 К примеру Если условие, связанное с ожидающая точка останова не удается проанализировать или оценить, предупреждение отправляется, что ожидающая точка останова не удается найти метод в настоящее время. Это может произойти, если код для точки останова еще не загружен.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

