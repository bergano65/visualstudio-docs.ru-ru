---
title: Реализация Тип Визуализаторы и пользовательских зрителей (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2ebbb5c8e27df4ae4baf2d9a9f1c3314188e2b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738505"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>Реализация тип визуализаторов и пользовательских зрителей
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Введите визуализаторы и пользовательские зрители позволяют пользователю просматривать данные определенного типа таким образом, что является более значимым, чем просто гексадецимальная свалка чисел. Оценщик выражения (EE) может связывать пользовательские аудитории с определенными типами данных или переменными. Эти пользовательские зрители реализованы EE. EE также может поддерживать внешние визуализаторы типа, которые могут поступать от другого стороннего поставщика или даже от конечном пользователя.

## <a name="discussion"></a>Обсуждение

### <a name="type-visualizers"></a>Ввизиолизаторы типа
 Visual Studio запрашивает список типовых визуализаторов и пользовательских зрителей для каждого объекта, который будет отображаться в окне часов. Оценщик выражения (EE) поставляет такой список для каждого типа, для которого он хочет поддерживать визуализаторы типа и пользовательских зрителей. Звонки [в GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) и [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) начинают весь процесс доступа к визуализаторам типа и пользовательским зрителям (см. [Визуализацию и Просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md) для получения подробной информации о последовательности вызовов).

### <a name="custom-viewers"></a>Пользовательские зрители
 Пользовательские зрители реализованы в EE для определенного типа данных и представлены интерфейсом [IDebugCustomViewer.](../../extensibility/debugger/reference/idebugcustomviewer.md) Пользовательский зритель не так гибок, как визуализатор типа, так как он доступен только тогда, когда EE, который реализует этот конкретный пользовательский зритель выполняет. Реализация пользовательского просмотра проще, чем реализация поддержки визуализаторов типов. Однако поддержка визуализаторов типа обеспечивает максимальную гибкость конечному пользователю для визуализации своих данных. Остальная часть этой дискуссии касается только визуализаторов типа.

## <a name="interfaces"></a>Интерфейсы
 EE реализует следующие интерфейсы для поддержки визуализаторов типа, которые будут использоваться Visual Studio:

- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)

- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)

- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)

- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

  EE потребляет следующие интерфейсы для поддержки визуализаторов типов:

- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)

- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)

- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)

## <a name="see-also"></a>См. также
- [Написание оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Визуализация и просмотр данных](../../extensibility/debugger/visualizing-and-viewing-data.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
