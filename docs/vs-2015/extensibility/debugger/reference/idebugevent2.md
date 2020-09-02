---
title: IDebugEvent2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f663be5910b342a6adba5da0b84d7e0d80cacc10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695413"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется для передачи критически важных отладочных данных, таких как остановка в точке останова, и некритически важных данных, например сообщения об отладке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) и поставщик пользовательского порта реализуют этот интерфейс на том же объекте, что и все остальные интерфейсы событий.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используя аргумент идентификатора интерфейса (IID), заданный для [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [события](../../../extensibility/debugger/reference/idebugportevents2-event.md), диспетчер отладки сеансов (SDM) вызывает [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) в `IDebugEvent2` интерфейсе для получения соответствующего интерфейса событий.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEvent2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Возвращает атрибуты для данного события отладки.|  
  
## <a name="remarks"></a>Remarks  
 Более конкретные интерфейсы событий, такие как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), не являются производными от интерфейса IDebugEvent2, но реализуются в виде отдельного интерфейса для того же объекта, что и `IDebugEvent2` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Журнале](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
