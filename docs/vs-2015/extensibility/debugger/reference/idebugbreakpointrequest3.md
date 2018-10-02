---
title: IDebugBreakpointRequest3 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 922c21c8d202f12a1ce06e049fd604c9e6d9b67a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568845"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugBreakpointRequest3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointrequest3).  
  
Этот интерфейс представляет сведения, необходимые для создания и привязки любого типа точки останова. Он является расширением [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Диспетчер отладки сеансов (SDM) обычно реализует этот интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Модуль отладки (DE) обращается к этот интерфейс путем вызова [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) об интерфейсе IDebugBreakpointRequest2, полученных при вызове [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, наследуемых от [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` интерфейс предоставляет следующий метод.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Получает сведения о запросе точки останова, описывающее этот запрос точки останова.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс используется для предоставления дополнительных сведений для DE через [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры. Эта дополнительная информация включает в себя идентификатор поставщика DE (в виде идентификатора GUID), имя точки трассировки и имя ограничения точки останова.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

