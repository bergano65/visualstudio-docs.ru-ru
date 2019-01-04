---
title: IEEVisualizerServiceProvider | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed17748a2c635de5b4a4b715d4061ee3841f18ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990442"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет доступ к методу, можно создать службу визуализатор, который используется для обработки задач визуализатора типа для интегрированной среды разработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для создания объекта службы визуализатор, который в свою очередь позволяет предоставить идентификаторы класса (`CLSID`s) из типа визуализаторы интегрированную среду разработки Visual Studio.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Средство оценки выражений (EE) вызывает [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Создает службу визуализатора|  
  
## <a name="remarks"></a>Примечания  
 `IEEVisualizerServiceProvider` Интерфейс получается во время реализации [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Служба визуализатора, который создает этот интерфейс позволяет предоставить возможность [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс, который EE отвечает за реализацию. EE также отвечает за реализацию [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс, позволяющий визуализаторов типов для просмотра и изменения значения свойства.  
  
 См. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) Дополнительные сведения о том, как взаимодействуют эти интерфейсы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)