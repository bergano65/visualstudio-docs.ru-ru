---
title: IPropertyProxyEESide | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8a75aa089d516f112d1c758cc161891aa26e0d2
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461079"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Этот интерфейс предоставляет методы для просмотра данных для связанного объекта. Этот интерфейс является частью поддержки визуализаторами типов.

## <a name="syntax"></a>Синтаксис

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Вычислитель выражений реализует этот интерфейс для поддержки визуализаторами типов.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения этого интерфейса. Вызовите [QueryInterface](/cpp/atl/queryinterface) на [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В этом интерфейсе реализованы следующие методы:

|Метод|Описание|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Инициализирует поставщик источника данных, таким образом, чтобы доступны данные объекта.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Извлекает сведения о сборке объекта.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Получает начальные данные для объекта.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Создает копию существующей с хранилищем данных.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Создает ссылку на существующее хранилище данных.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Извлекает сведения о конкретной сборки в контекст сборки, содержащей этот объект.|

## <a name="remarks"></a>Примечания
 Тип визуализатора использует этот интерфейс для доступа к значениям, связанный с объектом, который этот интерфейс является частью. Данных осуществляется через [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) интерфейс, который предоставляет представление только для чтения данных.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)