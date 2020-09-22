---
title: Иивисуализердатапровидер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86ad3f3ecec94c4c0773325ed2a571171b1f9b33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843253"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет возможность изменения значения объекта с помощью визуализатора типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для поддержки изменения данных в объекте свойства с помощью визуализатора типов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс используется при создании объекта [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) с помощью вызова [креатевисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Дополнительные сведения см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
  
|Метод|Description|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Определяет, можно ли обновить объект (и впоследствии его значение), который представляет этот визуализатор.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Вызывает повторное вычисление объекта для этого визуализатора.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Возвращает существующий объект для этого визуализатора (вычисление не выполняется).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Обновляет объект для этого визуализатора, тем самым изменяя значение, представленное визуализатором.|  
  
## <a name="remarks"></a>Remarks  
 Служба визуализатора (представленная интерфейсом [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) и возвращаемая методом [креатевисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) сохраняет ссылку на объект, реализующий `IEEVisualizerDataProvider` интерфейс. В результате `IEEVisualizerDataProvider` интерфейс не должен быть реализован на том же объекте, который реализует [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , если этот объект поддерживает ссылку на `IEEVisualizerService` объект: результаты циклической ссылки и взаимоблокировка возникает при уничтожении объектов. Рекомендуемым подходом является реализация `IEEVisualizerDataProvider` на отдельном объекте, к которому `IDebugProperty2` объект делегируется без вызова `IUnknown::AddRef` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [иивисуализерсервицепровидер](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
