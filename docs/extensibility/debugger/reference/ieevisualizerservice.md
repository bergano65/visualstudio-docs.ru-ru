---
title: IEEVisualizerService Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40d21dcc9b1da0e1e2250adcfad59b3ef46a2113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717943"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс реализует ключевые методы, которые поставляют функциональность интерфейсов [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) и [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerService : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio реализует этот интерфейс, чтобы позволить оценщику выражения (EE) поддерживать визуализаторы типа.

## <a name="notes-for-callers"></a>Заметки для абонентов
 EE призывает [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) получить этот интерфейс в рамках своей поддержки визуализаторов типов.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable

|Метод|Описание|
|------------|-----------------|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Получает количество пользовательских зрителей, о которых эта служба знает.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Получает список пользовательских зрителей.|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Возвращает прокси-объект для свойства.|
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Извлекает количество строк значения для отображения для указанного свойства или поля.|

## <a name="remarks"></a>Примечания
 IDE использует интерфейс [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) чтобы определить, есть ли пользовательские зрители или визуализаторы для свойства. Создавая сервис визуализаторов (с [CreateVisualizerService),](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)EE `IDebugProperty3` может предоставить функциональность интерфейсам и [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (которая поддерживает просмотр и изменение стоимости свойства) интерфейсов и тем самым поддерживать визуализаторы типа.

 Если EE имеет пользовательские зрителей, которые сам реализует, EE может прибывать `CLSID`с тех пользовательских зрителей в конце списка, возвращенного [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Это позволяет EE поддерживать как визуализаторы типа, так и собственных пользовательских зрителей. Просто убедитесь, что [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) отражает добавление любых пользовательских зрителей.

 Смотрите [Type Visualizer и пользовательский зритель](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) для обсуждения разницы между визуализаторами и зрителями.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
