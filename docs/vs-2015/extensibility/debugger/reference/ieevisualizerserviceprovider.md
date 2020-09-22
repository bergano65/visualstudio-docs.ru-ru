---
title: Иивисуализерсервицепровидер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9ba7c7216c590f773f1054a1f06cd3412ff6b20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842608"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет доступ к методу, который может создать службу визуализатора, которая используется для управления задачами визуализатора типов в интегрированной среде разработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для создания объекта службы визуализатора, который, в свою очередь, используется для предоставления идентификаторов классов для `CLSID` визуализаторов типов в интегрированной среде разработки Visual Studio.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Средство оценки выражений (EE) вызывает [жетисервице](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
  
|Метод|Description|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Создает службу визуализатора|  
  
## <a name="remarks"></a>Remarks  
 `IEEVisualizerServiceProvider`Интерфейс получается во время реализации [евалуатесинк](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Служба визуализатора, создаваемая этим интерфейсом, используется для предоставления функциональных возможностей интерфейсу [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , который отвечает за реализацию. EE также отвечает за реализацию интерфейса [иивисуализердатапровидер](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , который позволяет визуализаторам типов просматривать и изменять значения свойств.  
  
 Сведения о взаимодействии этих интерфейсов см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [евалуатесинк](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [иивисуализердатапровидер](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [жетисервице](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
