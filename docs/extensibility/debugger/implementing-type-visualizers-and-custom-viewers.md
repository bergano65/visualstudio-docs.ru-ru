---
title: Реализация визуализаторов типов и пользовательских средств просмотра | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9705555ad76663e1fb1bc402d5b050649d934ec
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411185"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Реализация визуализаторов типов и пользовательских средств просмотра
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Визуализаторов типов и пользовательских средств просмотра позволяют пользователю просматривать данные определенного типа в виде, более понятны, чем простой дамп шестнадцатеричных чисел. Вычислитель выражений (EE) можно связать пользовательские средства просмотра с определенными типами данных или переменные. Эти пользовательские средства просмотра реализуются путем EE. EE также может поддерживать внешний тип визуализаторы, которые могут поступать из другого стороннего поставщика или даже конечный пользователь.

## <a name="discussion"></a>Обсуждение

### <a name="type-visualizers"></a>Визуализаторы типа
 Visual Studio предлагает список визуализаторов типов и пользовательских средств просмотра для каждого объекта, который будет отображаться в окне контрольных значений. Вычислитель выражений (EE) предоставляет такой список для каждого типа, для которого он хочет поддержать визуализаторов типов и пользовательских средств просмотра. Вызовы [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) запустить весь процесс доступа к визуализаторов типов и пользовательских средств просмотра (см. в разделе [визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)сведения о последовательность вызова).

### <a name="custom-viewers"></a>Пользовательские средства просмотра
 Пользовательские средства просмотра реализуются в EE для определенного типа данных и представляются [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) интерфейс. Пользовательское средство просмотра не такие гибкие, как тип визуализатора, так как он доступен только в том случае, когда выполняется EE, реализующий этой конкретной пользовательское средство просмотра. Реализация пользовательское средство просмотра проще, чем реализация поддержки для визуализаторов типов. Тем не менее поддержка визуализаторов типов предоставляет максимальную гибкость для конечного пользователя для визуализации данных. Оставшейся части этого раздела касается только визуализаторами типов.

## <a name="interfaces"></a>интерфейсов,
 EE реализует следующие интерфейсы для поддержки типа визуализаторы, которые должны обрабатываться Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE использует следующие интерфейсы для поддержки визуализаторов типов:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>См. также
- [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)