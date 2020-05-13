---
title: IEEVisualizerServiceProvider (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717888"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс дает доступ к методу, который может создать службу визуализатора, которая используется для обработки задач визуализатора типов для IDE.

## <a name="syntax"></a>Синтаксис

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio реализует этот интерфейс для создания объекта службы визуализаторов,`CLSID`который, в свою очередь, используется для предоставления идентификаторов классов (ы) визуализаторов типа в Visual Studio IDE.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Оценщик выражений (EE) вызывает [GetEEService,](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable

|Метод|Описание|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Создает сервис визуализаторов|

## <a name="remarks"></a>Примечания
 Интерфейс `IEEVisualizerServiceProvider` получен во время реализации [EvaluateSync.](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Служба визуализаторов, которую создает этот интерфейс, используется для предоставления функциональности интерфейсу [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) который EE отвечает за реализацию. EE также отвечает за реализацию интерфейса [IEEVisualizerDataProvider,](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) который позволяет визуализаторам типа просматривать и изменять ценность свойства.

 Подробную информацию о том, как эти интерфейсы взаимодействуют, читайте в [визуализации и просмотре данных.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
