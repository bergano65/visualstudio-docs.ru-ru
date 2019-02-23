---
title: Визуализация и просмотр данных | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 852616ac77096a5b31078d64051f67f6cbb3ecb6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683382"
---
# <a name="visualizing-and-viewing-data"></a>Визуализация и просмотр данных
Визуализаторов типов и пользовательских средств просмотра представить данные способом, который быстро применяется для разработчика. Средство оценки выражений (EE) можно поддерживать визуализаторов сторонних типов, а также предоставить свои собственные пользовательские средства просмотра.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Определяет, сколько визуализаторов типов и пользовательских средств просмотра связаны с типом объекта, вызвав [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) метод. Если имеется хотя бы один тип визуализатора или пользовательское средство просмотра, Visual Studio вызывает [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) метод, чтобы получить список этих визуализаторы и средства просмотра (на самом деле, список, который реализует визуализаторы и средства просмотра) и представляет их пользователю.

## <a name="supporting-type-visualizers"></a>Поддержка визуализаторов типов
 Существует целый ряд интерфейсов, которые должны реализовывать EE для поддержки визуализаторами типов. Эти интерфейсы можно разделить на две большие категории: интерфейсы, в которых перечислены визуализаторов типов и интерфейсов, которые обращаются к данных свойства.

### <a name="listing-type-visualizers"></a>Список визуализаторов типов
 EE поддерживает список визуализаторов типов в своей реализации `IDebugProperty3::GetCustomViewerCount` и `IDebugProperty3::GetCustomViewerList`. Эти методы передачи вызова соответствующих методов [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) и [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) получается путем вызова [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Этот метод требует [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) интерфейс, который получается из [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) передается интерфейс [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` также требуется [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) и [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) интерфейсы, которые были переданы `IDebugParsedExpression::EvaluateSync`. Окончательный интерфейс, необходимый для создания `IEEVisualizerService` интерфейс [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс, который реализует EE. Этот интерфейс позволяет вносить изменения в свойство визуализации. Все свойства данные заключаются в [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) интерфейс, который реализуется также с помощью EE.

### <a name="accessing-property-data"></a>Доступ к данным свойство
 Доступ к данным свойство осуществляется с помощью [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс. Чтобы получить этот интерфейс, Visual Studio вызывает [QueryInterface](/cpp/atl/queryinterface) для свойства объекта, чтобы получить [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс (на тот же объект, реализующий [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) интерфейс), а затем вызывает [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) метод, чтобы получить `IPropertyProxyEESide` интерфейс.

 Все данные, передаваемые в `IPropertyProxyEESide` интерфейс, инкапсулировано в [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) интерфейс. Этот интерфейс представляет собой массив байтов и реализуется Visual Studio и EE. Если данные свойства должен быть изменен, Visual Studio создает `IEEDataStorage` объект, содержащий новые данные и вызовы [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) с этим объектом данных, чтобы получить новый `IEEDataStorage` объект, который в свою очередь, — передаваемый [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) для обновления данных свойства. `IPropertyProxyEESide::CreateReplacementObject` позволяет EE для создания экземпляра свой собственный класс, реализующий `IEEDataStorage` интерфейс.

## <a name="supporting-custom-viewers"></a>Поддержка пользовательских средств просмотра
 Флаг `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` задается в `dwAttrib` поле [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуры (возвращается путем вызова [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) чтобы указать, что объект имеет связанное пользовательское средство просмотра с ним. Если этот флаг установлен, Visual Studio получает [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) интерфейс из [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейса с помощью [QueryInterface](/cpp/atl/queryinterface).

 Если пользователь выбирает пользовательское средство просмотра, Visual Studio создает пользовательское средство просмотра с помощью средства просмотра `CLSID` предоставляемые `IDebugProperty3::GetCustomViewerList` метод. Visual Studio, затем вызывает [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) отображать значение для пользователя.

 Как правило `IDebugCustomViewer::DisplayValue` отображается только для чтения представление данных. Чтобы разрешить изменения в данных, EE необходимо реализовать пользовательский интерфейс, который поддерживает изменение данных в объект свойства. `IDebugCustomViewer::DisplayValue` Метод использует этот пользовательский интерфейс для поддержки изменения данных. Метод ищет пользовательский интерфейс `IDebugProperty2` интерфейса, переданный в качестве `pDebugProperty` аргумент.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Поддержка визуализаторов типов и пользовательских средств просмотра
 EE может поддерживать визуализаторов типов и пользовательских средств просмотра в [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) методы. Во-первых, EE добавляет число пользовательских средств просмотра, которые он предоставляет значение, возвращенное [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) метод. Во-вторых, добавляет EE `CLSID`s свои собственные пользовательские средства просмотра, в список, возвращаемый [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) метод.

## <a name="see-also"></a>См. также
- [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)
- [Визуализатор типов и пользовательское средство просмотра](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)