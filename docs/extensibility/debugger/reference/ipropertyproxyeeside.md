---
title: IPropertyProxyEEside (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714862"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Этот интерфейс предоставляет методы для просмотра данных на связанном объекте. Этот интерфейс является частью поддержки визуализаторов типов.

## <a name="syntax"></a>Синтаксис

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс для поддержки визуализаторов типов.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [GetPropertyProxy,](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) чтобы получить этот интерфейс. Для получения интерфейса [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) позвоните [в queryInterface](/cpp/atl/queryinterface) на [интерфейсе IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Следующие методы реализуются этим интерфейсом:

|Метод|Описание|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Инициализирует поставщика источников данных, чтобы можно было получить доступ к данным объекта.|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Извлекает информацию о сборке объекта.|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Получает исходные данные для объекта.|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Создает копию существующего хранилища данных.|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Создает ссылку на существующее хранилище данных.|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Извлекает информацию о конкретной сборке в контексте сборки, содержащей этот объект.|

## <a name="remarks"></a>Примечания
 Визуализатор типа использует этот интерфейс для доступа к значениям, связанным с объектом, частью которого является этот интерфейс. Доступ к данным осуществляется через интерфейс [IEEDataStorage,](../../../extensibility/debugger/reference/ieedatastorage.md) который обеспечивает только для чтения представление данных.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
