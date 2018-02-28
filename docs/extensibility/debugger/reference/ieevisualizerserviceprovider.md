---
title: "IEEVisualizerServiceProvider | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d778ba9038a9d14c7bb107f239adbc0d9bab2b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет доступ к метода, который можно создать визуализатор службы, которая используется для обработки задач типов визуализатор для интегрированной среды разработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для создания объекта службы визуализатор, который в свою очередь, используется для предоставления идентификаторы класса (`CLSID`s) тип визуализаторов интегрированную среду разработки Visual Studio.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Средство оценки выражений (Эстония) вызывает [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) для получения этого интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Создает службу визуализатора|  
  
## <a name="remarks"></a>Примечания  
 `IEEVisualizerServiceProvider` Интерфейс получается во время реализации [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Служба визуализатора, которая создает этот интерфейс используется для предоставления функциональные возможности для [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс, EE отвечает за реализацию. EE также отвечает за реализацию [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс, позволяющий визуализаторами типов для просмотра и изменения значения свойства.  
  
 В разделе [Visualizing и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) сведения о том, как взаимодействуют эти интерфейсы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)