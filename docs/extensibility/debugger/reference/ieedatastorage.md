---
title: IEEDataStorage (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718187"
---
# <a name="ieedatastorage"></a>IEEDataStorage
Этот интерфейс представляет собой массив байтов.

## <a name="syntax"></a>Синтаксис

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения (EE) реализует этот интерфейс, чтобы представлять массив байтов (используется визуализаторами типа для извлечения и изменения данных через интерфейс [IPropertyProxyEESide).](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) EE обычно реализует этот интерфейс для поддержки внешних визуализаторов типа.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Методы на `IPropertyProxyEESide` интерфейсе все вернуть этот интерфейс. Позвоните [GetPropertyProxy,](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) чтобы получить интерфейс [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Для получения интерфейса [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) позвоните [в queryInterface](/cpp/atl/queryinterface) на [интерфейсе IDebugProperty3.](../../../extensibility/debugger/reference/idebugproperty3.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Интерфейс `IEEDataStorage` реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Извлекает указанное количество байтов данных в поставляемый буфер.|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Извлекает количество доступных байтов данных.|

## <a name="remarks"></a>Примечания
 Этот интерфейс используется визуализатором типа для доступа к данным, хранящимся на определенном объекте. Данные рассматриваются как массив байтов, что позволяет визуализатору типа манипулировать им любым способом, необходимым для представления его пользователю.

 Пользовательский зритель может также использовать этот интерфейс, при желании, хотя и более типично, пользовательский зритель будет использовать пользовательский интерфейс, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) или [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (для строки ориентированных данных).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
