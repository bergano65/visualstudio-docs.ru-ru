---
title: IEEVisualizerDataProvider | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 269f154083f3589e989a6ca2f9ce0835b249181a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350181"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс обеспечивает возможность менять значения объекта через тип визуализатора.

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для поддержки изменения данных на объект свойства через тип визуализатора.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс используется при создании [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) объекта путем вызова [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). См. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) для получения дополнительных сведений.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable

|Метод|Описание|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Определяет, является ли возможность обновления объекта (и следовательно, его значение), представляющий этот визуализатор.|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Вызывает принудительное повторное вычисление значения объекта для этот визуализатор.|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Получает существующий объект для этот визуализатор (не оценка выполняется).|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Обновляет объект для этот визуализатор, тем самым изменив значение, которое представляет визуализатор.|

## <a name="remarks"></a>Примечания
 Служба визуализатора (представленные как [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) интерфейс и возвращенный [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) хранит ссылки на объект, реализующий интерфейс `IEEVisualizerDataProvider` интерфейс . В результате `IEEVisualizerDataProvider` не следует реализовывать интерфейс на тот же объект, реализующий [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Если этот объект сохраняет ссылку на `IEEVisualizerService` объект: результаты циклическую ссылку и Взаимоблокировка возникает, когда объекты уничтожаются. Рекомендуемый подход заключается в реализации `IEEVisualizerDataProvider` в отдельном объекте, к которому `IDebugProperty2` объекта делегаты без вызова `IUnknown::AddRef` на нем.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)