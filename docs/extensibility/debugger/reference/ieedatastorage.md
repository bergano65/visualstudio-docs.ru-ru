---
title: IEEDataStorage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeb34d9574a6070b2d1f658575d345d74aa72972
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915256"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Этот интерфейс представляет собой массив байтов.

## <a name="syntax"></a>Синтаксис

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений (EE) реализует этот интерфейс для представления массива байтов (используемый тип визуализаторы для извлечения и изменения данных в [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс). EE обычно реализует этот интерфейс для поддержки визуализаторы внешнего типа.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Методы в `IPropertyProxyEESide` интерфейс все возвращают этот интерфейс. Вызовите [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) для получения [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) интерфейс. Вызовите [QueryInterface](/cpp/atl/queryinterface) на [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс для получения [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 `IEEDataStorage` Интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Извлекает указанное число байтов данных, предоставленный буфер.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Возвращает число доступных байтов данных.|

## <a name="remarks"></a>Примечания
 Этот интерфейс используется тип визуализатора для доступа к данным, удерживаемые определенного объекта. Эти данные обрабатываются как массив байт, обеспечивая визуализатор типов работать с ним так, как требуется, чтобы представить его пользователю.

 Пользовательское средство просмотра можно также использовать этот интерфейс, при необходимости, несмотря на то, что как правило, использовать настраиваемый интерфейс, пользовательское средство просмотра [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) или [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (для данных, ориентированных на строку).

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)