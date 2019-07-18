---
title: IPropertyProxyProvider | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbda02c26018adc4e5f1f3677b75bc2dce25a2e5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339290"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Этот интерфейс предоставляет интерфейс-посредник для просмотра и изменения данных объекта.

## <a name="syntax"></a>Синтаксис

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений (EE) реализует этот интерфейс на тот же объект, реализующий [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс как часть поддержки EE визуализаторами типов.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProperty3` интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 `IPropertyProxyProvider` Интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Извлекает свойство прокси-интерфейса для просмотра данных для объекта.|

## <a name="remarks"></a>Примечания
 Несмотря на то, что EE реализует этот интерфейс, реализация [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) обычно обрабатываются [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). См. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) Дополнительные сведения о получении IEEVisualizerService интерфейс.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)