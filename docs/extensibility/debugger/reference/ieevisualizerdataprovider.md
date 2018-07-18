---
title: IEEVisualizerDataProvider | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e37561957d592ecd9ae855f2816c860f84e7b20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121226"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет возможность изменения значения объекта через тип визуализатора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для поддержки изменения данных в объекте свойство через тип визуализатора.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс используется при создании [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) объекта путем вызова [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). В разделе [Visualizing и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) для получения дополнительных сведений.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Определяет, является ли возможность обновления объекта (и следовательно, его значение), представляющий этот визуализатор.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Вызывает принудительное повторное вычисление объект для данного визуализатора.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Возвращает объект, существующие для данного визуализатора (вычисление не выполняется).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Обновляет объект для данного визуализатора, тем самым изменив значение, которое представляет визуализатора.|  
  
## <a name="remarks"></a>Примечания  
 Службы визуализатора (представленные как [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) интерфейс, а также возвращаемые [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) хранит ссылки на объект, реализующий `IEEVisualizerDataProvider` интерфейса . В результате `IEEVisualizerDataProvider` не следует реализовывать на тот же объект, реализующий интерфейс [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Если этот объект сохраняет ссылку на `IEEVisualizerService` объект: результаты циклическую ссылку и Взаимоблокировка возникает, когда объекты удаляются. Рекомендуется реализовать `IEEVisualizerDataProvider` на отдельный объект, к которому `IDebugProperty2` объекта делегаты без вызова `IUnknown::AddRef` на нем.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)