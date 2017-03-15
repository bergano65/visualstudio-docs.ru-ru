---
title: "Визуализация и просмотр данных | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], просмотр данных"
  - "отладка [пакет SDK для отладки], визуализация данных"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Визуализация и просмотр данных
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Введите сведения о пользовательских визуализаторов и средств просмотра, присутствующие в способом, который может применяться к разработчику быстро.  Средство оценки выражений \(EE\) может поддерживать сторонние визуализаторы типа, так же как предоставить собственных пользовательских средств просмотра.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] определяет, сколько визуализаторы типа и пользовательских средств просмотра, связанных с типом объекта, вызвав  [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) метод.  Если хотя бы одного типа визуализатора доступный или пользовательские средства просмотра, Visual Studio вызывает [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) метод, чтобы получить список визуализаторов и средств просмотра \(фактически, список  `CLSID`s, которые реализуют визуализаторы и средств просмотра\) и представляет их пользователю.  
  
## Поддержка визуализаторы типа  
 Несколько интерфейсов, EE должен реализовать для поддержки визуализаторы типа.  Эти интерфейсы можно разбить на 2 большие категории: те, которые перечислены визуализаторы типа и те, которые получают доступ к данным о свойствах.  
  
### Визуализаторы типа перечисления  
 EE поддерживает список визуализаторов типа в своей реализации `IDebugProperty3::GetCustomViewerCount` и  `IDebugProperty3::GetCustomViewerList`.  Эти методы возвращают вызов соответствующего методам [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) и  [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) получает путем вызова  [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md).  Этот метод требует [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) интерфейс, который получен из  [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) интерфейс, передаваемый  [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  `IEEVisualizerServiceProvider::CreateVisualizerService` также требует  [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) и  [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) интерфейсы, вызываемые, переданного  `IDebugParsedExpression::EvaluateSync`.  Последний интерфейс, необходимый для создания `IEEVisualizerService` интерфейс  [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс, который реализует EE.  Этот интерфейс позволяет изменения, которые необходимо выполнить в визуализированным свойству.  Все данные инкапсулированы в свойства IDebugObject интерфейс, который также реализован EE.  
  
### Доступ к данным свойства  
 Доступ к данным осуществляется через свойства [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс.  Получить этот интерфейс, вызывается Visual Studio [QueryInterface](/visual-cpp/atl/queryinterface) в объекте возвращаемого свойства  [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс, реализованный на одном \(объекта, реализующего  [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) интерфейс\) и затем вызывает метод  [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) метод получения  `IPropertyProxyEESide` интерфейс.  
  
 Все данные, передаваемые в действие и из `IPropertyProxyEESide` интерфейс встроен в  [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) интерфейс.  Этот интерфейс представляет массив байтов и реализуется как Visual Studio, так и EE.  Если данные свойства изменением, Visual Studio создает `IEEDataStorage` объект инициирующей новые данные, а вызовы  [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) с этим объектом данных для получения новой  `IEEDataStorage` объект, который, в свою очередь, передает в  [InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md) обновление данных свойства.  `IPropertyProxyEESide::CreateReplacementObject` разрешает EE создать собственный класс, реализующий  `IEEDataStorage` интерфейс.  
  
## Поддержка пользовательские средства просмотра  
 Пометить `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` набор  `dwAttrib` поле   [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) структура \(возвращаемую вызовом  [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\), чтобы указать, что объект имеет пользовательского средства просмотра связать с ним.  Если пометить установлен, Visual Studio возвращает [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) интерфейс из  [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс использование  [QueryInterface](/visual-cpp/atl/queryinterface).  
  
 Если пользователь выбирает пользовательское средство просмотра, Visual Studio создает пользовательское средство просмотра с помощью средства просмотра `CLSID` поддерживается  `IDebugProperty3::GetCustomViewerList` метод.  Вызовы затем Visual Studio [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) указать значения для пользователя.  
  
 Обычно `IDebugCustomViewer::DisplayValue` представляет доступную только для чтения представление данных.  Чтобы разрешить изменения к данным, EE должен реализовать пользовательский интерфейс, который поддерживает изменение данных в объекте свойства.  `IDebugCustomViewer::DisplayValue` метод использует этот пользовательский интерфейс для поддержки изменения данных.  Метод ищет пользовательский интерфейс `IDebugProperty2` интерфейс переданный как  `pDebugProperty` аргумент.  
  
## Поддержка и визуализаторы типа и пользовательские средства просмотра  
 EE может поддерживать и визуализаторы типа и пользовательских средств просмотра в [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) и  [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) методы.  Во\-первых, EE добавляет количество пользовательских средств просмотра, он передает значение, возвращенное [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) метод.  Во\-вторых, EE добавить `CLSID`s собственных пользовательских средств просмотра в список возвращенных  [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) метод.  
  
## См. также  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)