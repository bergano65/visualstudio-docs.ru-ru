---
title: "IEEVisualizerService | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97701dede6a3e6b17911f6ab3c5e37dfdd90cc58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс реализует основные методы, которые предоставляют функциональные возможности для [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейсов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс, позволяющий вычислитель выражений (Эстония) для поддержки визуализаторами типов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовы EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) получить этот интерфейс в рамках поддержки для визуализаторами типов.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Возвращает число пользовательских средств просмотра, о которых известно, эта служба.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Получает список пользовательских средств просмотра.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Возвращает объект прокси-сервера для свойства.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Возвращает номер строки значение указанного свойства или поля.|  
  
## <a name="remarks"></a>Примечания  
 Интегрированная среда разработки использует [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс, чтобы определить наличие любые пользовательские средства просмотра или введите визуализаторы для свойства. Путем создания визуализатора службы (с [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), EE может предоставить возможность `IDebugProperty3` и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (который поддерживает просмотр и изменение значение свойства), интерфейсы и тем самым поддерживают визуализаторами типов.  
  
 Если EE пользовательских средств просмотра реализует, в свою очередь, могут добавляться к EE `CLSID`s из этих пользовательских средств просмотра, в конец списка, возвращенных [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Это позволяет EE для поддержки визуализаторами типов и свои собственные пользовательские средства просмотра. Просто убедитесь, что [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) получающийся при добавлении любые пользовательские средства просмотра.  
  
 В разделе [тип визуализатора и пользовательского средства просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) обсуждение разницу между визуализаторы, а также средства просмотра.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)