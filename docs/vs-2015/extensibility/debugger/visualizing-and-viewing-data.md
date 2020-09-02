---
title: Визуализация и просмотр данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 719a2b3d073d90ff3977496c7f98ebecb1ab48a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696313"
---
# <a name="visualizing-and-viewing-data"></a>Визуализация и просмотр данных
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Визуализаторы типов и пользовательские средства просмотра представляют данные в удобном для разработчика виде. Средство оценки выражений (EE) может поддерживать визуализаторы типов сторонних производителей, а также предоставлять собственные пользовательские средства просмотра.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Определяет, сколько визуализаторов типов и пользовательских средств просмотра связаны с типом объекта путем вызова метода [жеткустомвиеверкаунт](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) . Если имеется хотя бы один визуализатор типов или пользовательское средство просмотра, Visual Studio вызывает метод [жеткустомвиеверлист](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) для получения списка этих визуализаторов и средств просмотра (на самом деле, списка `CLSID` , которые реализуют визуализаторы и средства просмотра) и представляют их пользователю.  
  
## <a name="supporting-type-visualizers"></a>Вспомогательные визуализаторы типов  
 Существует ряд интерфейсов, которые должны быть реализованы в EE для поддержки визуализаторов типов. Эти интерфейсы можно разделить на две основные категории: те, в которых перечислены визуализаторы типов, и те, которые обращаются к данным свойств.  
  
### <a name="listing-type-visualizers"></a>Список визуализаторов типов  
 EE поддерживает вывод списка визуализаторов типов в его реализации `IDebugProperty3::GetCustomViewerCount` и `IDebugProperty3::GetCustomViewerList` . Эти методы передают вызов соответствующим методам [жеткустомвиеверкаунт](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) и [жеткустомвиеверлист](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [Иивисуализерсервице](../../extensibility/debugger/reference/ieevisualizerservice.md) получается путем вызова [креатевисуализерсервице](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Для этого метода требуется интерфейс [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , полученный из интерфейса [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) , переданного в [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` также требуются интерфейсы [идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md) и [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md) , которые были переданы в `IDebugParsedExpression::EvaluateSync` . Последним интерфейсом, необходимым для создания `IEEVisualizerService` интерфейса, является интерфейс [иивисуализердатапровидер](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , который реализуется в ee. Этот интерфейс позволяет вносить изменения в свойство визуализации. Все данные свойств инкапсулируются в интерфейсе [идебугобжект](../../extensibility/debugger/reference/idebugobject.md) , который также реализуется в ee.  
  
### <a name="accessing-property-data"></a>Доступ к данным свойств  
 Доступ к данным свойства осуществляется через интерфейс [ипропертипроксеесиде](../../extensibility/debugger/reference/ipropertyproxyeeside.md) . Чтобы получить этот интерфейс, Visual Studio вызывает [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для объекта Property, чтобы получить интерфейс [ипропертипроксипровидер](../../extensibility/debugger/reference/ipropertyproxyprovider.md) (реализованный в том же объекте, который реализует интерфейс [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) ), а затем вызывает метод [жетпропертипрокси](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения `IPropertyProxyEESide` интерфейса.  
  
 Все данные, передаваемые в интерфейс и из него `IPropertyProxyEESide` , инкапсулируются в интерфейсе [иидатастораже](../../extensibility/debugger/reference/ieedatastorage.md) . Этот интерфейс представляет массив байтов и реализуется как в Visual Studio, так и в EE. При изменении данных свойства Visual Studio создает `IEEDataStorage` объект, содержащий новые данные, и вызывает [функция createreplacementobject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) с этим объектом данных, чтобы получить новый `IEEDataStorage` объект, который, в свою очередь, передается в [инплацеупдатеобжект](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) для обновления данных свойства. `IPropertyProxyEESide::CreateReplacementObject` позволяет компоненту EE создать экземпляр собственного класса, реализующего `IEEDataStorage` интерфейс.  
  
## <a name="supporting-custom-viewers"></a>Поддержка пользовательских средств просмотра  
 Флаг `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` задается в `dwAttrib` поле структуры [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) (возвращается вызовом [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)), чтобы указать, что с объектом связано пользовательское средство просмотра. Если этот флаг установлен, Visual Studio получает интерфейс [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) из интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) с помощью [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3).  
  
 Если пользователь выбирает пользовательское средство просмотра, Visual Studio создает экземпляр пользовательского средства просмотра с помощью средства просмотра, `CLSID` предоставленного `IDebugProperty3::GetCustomViewerList` методом. Затем Visual Studio вызывает [дисплайвалуе](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) , чтобы отобразить значение для пользователя.  
  
 Обычно `IDebugCustomViewer::DisplayValue` представляет собой представление данных, доступное только для чтения. Чтобы разрешить изменения данных, в EE должен быть реализован пользовательский интерфейс, поддерживающий изменение данных в объекте свойства. `IDebugCustomViewer::DisplayValue`Метод использует этот пользовательский интерфейс для поддержки изменения данных. Метод выполняет поиск пользовательского интерфейса в `IDebugProperty2` интерфейсе, переданном в качестве `pDebugProperty` аргумента.  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Поддержка визуализаторов типов и пользовательских средств просмотра  
 EE может поддерживать как визуализаторы типов, так и пользовательские средства просмотра в методах [жеткустомвиеверкаунт](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [жеткустомвиеверлист](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) . Во-первых, EE добавляет число пользовательских средств просмотра, которые он передает, в значение, возвращаемое методом [жеткустомвиеверкаунт](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) . Во вторых, EE добавляет к `CLSID` списку, возвращенному методом [жеткустомвиеверлист](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) , собственные пользовательские средства просмотра.  
  
## <a name="see-also"></a>См. также:  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
