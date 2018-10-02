---
title: IDebugBreakpointResolution2 | Документация Майкрософт
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
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db70a0c1a65ce369810f3fc3753baed10e3682a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563890"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugBreakpointResolution2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointresolution2).  
  
Этот интерфейс представляет данные, описывающие связанная точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointResolution2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс как часть поддержки точек останова. Этот интерфейс предоставляет описание связанная точка останова, диспетчер отладки сеансов при просмотре свойств точки останова.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBreakpointResolution2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Получает тип точки останова, представленный данным разрешением.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Возвращает сведения о разрешении точки останова, описывающий эту точку останова.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)

