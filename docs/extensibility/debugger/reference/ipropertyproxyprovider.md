---
title: IPropertyProxyProvider | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1e9afbe99e6265e47bf033c7d4af8e93590aaf6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718265"
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

|Метод|Описание:|
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