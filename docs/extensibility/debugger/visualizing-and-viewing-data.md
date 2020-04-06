---
title: Визуализация и просмотр данных Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b5f984e6c6a3c1c8f3835dfa93a8679ae16680a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712378"
---
# <a name="visualizing-and-viewing-data"></a>Визуализация и просмотр данных
Введите визуализаторы и пользовательские зрители представляют данные таким образом, чтобы быстро значимым для разработчика. Оценщик выражения (EE) может поддерживать сторонние визуализаторы типа, а также поставлять своих собственных пользовательских зрителей.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]определяет, сколько визуализаторов и пользовательских зрителей связаны с типом объекта, позвонив в метод [GetCustomViewerCount.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Если есть по крайней мере один тип визуализатора или пользовательский зритель доступен, Visual Studio называет [метод GetCustomViewerList,](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) чтобы получить список этих визуализаторов и зрителей (на самом деле, список s, который реализует визуализаторы и зрителей) и представляет их пользователю.

## <a name="supporting-type-visualizers"></a>Поддерживающие визуализаторы типа
 Существует ряд интерфейсов, которые EE должен реализовать для поддержки визуализаторов типов. Эти интерфейсы можно разбить на две широкие категории: интерфейсы, в которые перечисляется визуализаторы типа, и интерфейсы, которые получают доступ к данным свойств.

### <a name="listing-type-visualizers"></a>Визуализаторы типа листинга
 EE поддерживает перечисление визуализаторов типа в его реализации `IDebugProperty3::GetCustomViewerCount` и `IDebugProperty3::GetCustomViewerList`. Эти методы передают вызов соответствующим методам [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) и [GetCustomViewerList.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) получена по телефону [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Этот метод требует интерфейса [IDebugBinder3,](../../extensibility/debugger/reference/idebugbinder3.md) который получен из интерфейса [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) передаваемого [в EvaluateSync.](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) `IEEVisualizerServiceProvider::CreateVisualizerService`также требует [iDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) и [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) интерфейсы, `IDebugParsedExpression::EvaluateSync`которые были переданы . Окончательный интерфейс, необходимый для создания `IEEVisualizerService` интерфейса [iEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс, который EE реализует. Этот интерфейс позволяет вносить изменения в визуализированное свойство. Все данные свойств инкапсулируются в интерфейсе [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) который также реализован EE.

### <a name="accessing-property-data"></a>Доступ к данным свойств
 Доступ к данным о собственности осуществляется через интерфейс [IPropertyProxyEESide.](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Чтобы получить этот интерфейс, Visual Studio вызывает [queryInterface](/cpp/atl/queryinterface) на объекте свойств, чтобы получить интерфейс [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (реализован ный объект, который реализует интерфейс `IPropertyProxyEESide` [IDebugProperty3),](../../extensibility/debugger/reference/idebugproperty3.md) а затем вызывает метод [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения интерфейса.

 Все данные, передаваемые в `IPropertyProxyEESide` интерфейс и выход из нее, инкапсулируются в интерфейсе [IEEDataStorage.](../../extensibility/debugger/reference/ieedatastorage.md) Этот интерфейс представляет собой массив байтов и реализуется как Visual Studio, так и EE. При изменении данных объекта Visual Studio создает `IEEDataStorage` объект, удерживающий новые данные, и вызывает [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) с этим объектом данных, чтобы получить новый `IEEDataStorage` объект, который, в свою очередь, передается [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) для обновления данных объекта. `IPropertyProxyEESide::CreateReplacementObject`позволяет EE мгновенно готизовать свой собственный `IEEDataStorage` класс, который реализует интерфейс.

## <a name="supporting-custom-viewers"></a>Поддержка пользовательских зрителей
 Флаг `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` устанавливается в `dwAttrib` поле [структуры DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (возвращается по вызову [в GetPropertyInfo),](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)чтобы указать, что объект имеет пользовательский зритель, связанный с ним. Когда этот флаг установлен, Visual Studio получает интерфейс [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) из интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) с помощью [queryInterface.](/cpp/atl/queryinterface)

 Если пользователь выбирает пользовательского просмотра, Visual Studio мгновенно настраивает пользовательского `CLSID` зрителя `IDebugProperty3::GetCustomViewerList` с помощью предоставленного методом зрителя. Visual Studio затем вызывает [DisplayValue,](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) чтобы показать значение для пользователя.

 Как правило, `IDebugCustomViewer::DisplayValue` представлено только для чтения представление данных. Чтобы позволить вносить изменения в данные, EE должен реализовать пользовательский интерфейс, поддерживающий изменение данных на объекте свойств. Метод `IDebugCustomViewer::DisplayValue` использует этот пользовательский интерфейс для поддержки изменения данных. Метод ищет пользовательский интерфейс `IDebugProperty2` на интерфейсе, `pDebugProperty` передаваемом в качестве аргумента.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Поддержка как тип визуализаторов и пользовательских зрителей
 EE может поддерживать как тип визуализаторов, так и пользовательских зрителей в методах [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [GetCustomViewerList.](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Во-первых, EE добавляет количество пользовательских зрителей, которые он поставляет на значение, возвращенное методом [GetCustomViewerCount.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Во-вторых, EE `CLSID`придает с его собственным пользовательским зрителям список, возвращенный методом [GetCustomViewerList.](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="see-also"></a>См. также
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
- [Введите визуализатор и пользовательский зритель](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
