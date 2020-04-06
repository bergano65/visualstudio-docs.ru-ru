---
title: IEnumDebugPropertyInfo2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715354"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
Этот интерфейс перечисляет [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуры.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс для представления информации для конкретного свойства.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [ВИNumChildren,](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) чтобы получить интерфейс, представляющий детей определенного свойства. Позвоните [EnumProperties,](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) чтобы получить этот интерфейс, представляющий свойства определенного кадра стека.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugPropertyInfo2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|Извлекает определенное количество [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|Пропускает определенное количество [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|Получает количество [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структур в регистраторе.|

## <a name="remarks"></a>Примечания
 В целом свойство — это иерархия информации, которая может включать имя, значение, адрес и тип, а также любую другую информацию, соответствующую соответствующему объекту свойств или кадровому штабу. Более подробную информацию можно узнать в [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
