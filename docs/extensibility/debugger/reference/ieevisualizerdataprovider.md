---
title: "IEEVisualizerDataProvider | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider
helpviewer_keywords: IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ffe7e33b4652c0f0d3bd506e28d14c5b0949983
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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