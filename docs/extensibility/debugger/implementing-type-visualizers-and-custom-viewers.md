---
title: "Реализация визуализаторами типов и пользовательских средств просмотра | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19718425df6f0c8a656db0e3d7ebf0f06937f780
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Реализация визуализаторами типов и пользовательские средства просмотра
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Тип визуализаторы и пользовательские средства просмотра позволяют пользователю просматривать данные определенного типа в виде, более понятны, чем простой дамп шестнадцатеричных чисел. Вычислитель выражений (Эстония) можно связать пользовательские средства просмотра с помощью определенных типов данных или переменных. Эти пользовательские средства просмотра реализуются EE. EE также могут поддерживать визуализаторы внешнего типа, которые могут поступать из другого стороннего поставщика или даже конечного пользователя.  
  
## <a name="discussion"></a>Обсуждение  
  
### <a name="type-visualizers"></a>Визуализаторы типа  
 Visual Studio запрашивает список визуализаторами типов и пользовательские средства просмотра для каждого объекта, для отображения в окне контрольных значений. Вычислитель выражений (Эстония) предоставляет список для каждого типа, для которого необходимо поддерживать визуализаторами типов и пользовательских средств просмотра. Вызовы [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) запустить весь процесс доступа к визуализаторами типов и пользовательских средств просмотра (в разделе [Visualizing и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)сведения о последовательность вызова).  
  
### <a name="custom-viewers"></a>Пользовательские средства просмотра  
 Пользовательские средства просмотра, реализованных в EE для определенного типа данных и представляются [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) интерфейса. Так как он доступен только в том случае, когда выполняется EE, который реализует пользовательское средство просмотра, определенной пользовательское средство просмотра не же гибкостью, что тип визуализатора. Реализация пользовательское средство просмотра проще, чем реализовать поддержку визуализаторами типов. Тем не менее поддержка визуализаторами типов предоставляет максимальную гибкость для конечного пользователя для визуализации данных или ее. В оставшейся части данного обсуждения касается только визуализаторами типов.  
  
## <a name="interfaces"></a>Интерфейсы  
 EE реализует следующие интерфейсы для поддержки визуализаторами типов, для использования в Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE использует следующие интерфейсы для поддержки визуализаторами типов:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)