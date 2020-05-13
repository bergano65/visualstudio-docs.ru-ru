---
title: IEEVisualizerDataProvider (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718050"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс обеспечивает возможность изменения значения объекта с помощью визуализатора типа.

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс для поддержки изменения данных об объекте свойства с помощью визуализатора типа.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс используется при создании объекта [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) через звонок [в CreateVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) Более подробную информацию можно узнать из [визуализации и просмотра данных.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable

|Метод|Описание|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Определяет, возможно ли обновить объект (а затем и его значение), что этот визуализатор представляет.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Заставляет переоценку объекта для этого визуализатора.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Получает существующий объект для этого визуализатора (оценка не выполняется).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Обновляет объект для этого визуализатора, тем самым изменяя значение, представленное визуализатором.|

## <a name="remarks"></a>Примечания
 Служба визуализаторов (представленная интерфейсом [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) и возвращенная [CreateVisualizerService)](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) `IEEVisualizerDataProvider` содержит ссылку на объект, реализующий интерфейс. В результате `IEEVisualizerDataProvider` интерфейс не должен реализовываться на том же объекте, который реализует [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) если этот объект поддерживает ссылку на `IEEVisualizerService` объект: при уничтожении объектов возникают круговые результаты ссылки и взаимоблокировка. Рекомендуемый подход заключается в реализации `IEEVisualizerDataProvider` `IDebugProperty2` на отдельном `IUnknown::AddRef` объекте, на который объект делегирует, не вызывая его.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
