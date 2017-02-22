---
title: "Реализация типа визуализаторы и пользовательские средства просмотра | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], пользовательское средство просмотра"
  - "отладка [отладка SDK] типа визуализатора"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Реализация типа визуализаторы и пользовательские средства просмотра
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Тип визуализаторы и пользовательские средства просмотра разрешить пользователю просматривать данные определенного типа в виде, более понятны, чем простой дамп шестнадцатеричных чисел. Вычислитель выражений \(EE\) можно связать пользовательские средства просмотра с определенными типами данных или переменные. Эти пользовательские средства просмотра реализуются EE. EE также поддерживает внешний тип визуализаторы, которые могут поступать из другого стороннего поставщика или даже конечного пользователя.  
  
## Обсуждение  
  
### Визуализаторы типа  
 Visual Studio запрашивает список визуализаторов типа и пользовательские средства просмотра для каждого объекта для отображения в окне контрольных значений. Вычислитель выражений \(EE\) предоставляет список для каждого типа, для которого необходимо поддерживать тип визуализаторы и пользовательские средства просмотра. Вызовы функций [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) и [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Начать весь доступ к визуализаторам типа и пользовательские средства просмотра \(см. [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md) сведения о последовательности вызова\).  
  
### Пользовательские средства просмотра  
 Пользовательские средства просмотра реализуются в EE для определенного типа данных и представляются [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) интерфейса. Пользовательское средство просмотра не такой гибкий, как тип визуализатора, так как он доступен только при выполнении EE, который реализует пользовательское средство просмотра, определенного. Реализация пользовательского средства просмотра проще, чем реализовать поддержку типа визуализаторы. Тем не менее поддержка визуализаторы тип предоставляет максимальную гибкость для конечного пользователя для визуализации данных или ее. Оставшаяся часть этого обсуждения касается только тип визуализаторы.  
  
## Интерфейсы  
 EE реализует следующие интерфейсы для поддержки визуализаторы тип, используемый Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE использует следующие интерфейсы для поддержки визуализаторы типа:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)