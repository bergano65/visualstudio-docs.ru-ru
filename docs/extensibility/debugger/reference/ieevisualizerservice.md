---
title: IEEVisualizerService | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3c9cff6b4de172e9331057bb56a39a87e8b6ab0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310119"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс реализует основные методы, которые предоставляют функциональные возможности для [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейсов.

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс, позволяющий вычислитель выражений (EE) для поддержки визуализаторами типов.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовы EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) для получения визуализаторов типов этот интерфейс как часть его поддержки.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable

|Метод|Описание|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Возвращает число пользовательских средств просмотра, о которых знает данная служба.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Извлекает список пользовательских средств просмотра.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Возвращает объект прокси для свойства.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Возвращает номер строки значение указанного свойства или поля.|

## <a name="remarks"></a>Примечания
 Интегрированная среда разработки использует [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс, чтобы определить, есть ли любые пользовательские средства просмотра или введите визуализаторы для свойства. Создав службу визуализатор (с [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), EE может предоставить возможность `IDebugProperty3` и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (который поддерживает просмотр и изменение значение свойства), интерфейсы и тем самым поддерживают визуализаторами типов.

 Если EE пользовательских средств просмотра, в свою очередь реализует, можно добавить EE `CLSID`s из этих пользовательских средств просмотра, в конец списка, возвращаемые [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Это позволяет EE для поддержки визуализаторов типов и свои собственные пользовательские средства просмотра. Просто убедитесь, что [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) получающаяся при добавлении любые пользовательские средства просмотра.

 См. в разделе [визуализатор типов и пользовательские средства просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) обсуждение разницу между визуализаторы, а также средства просмотра.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)