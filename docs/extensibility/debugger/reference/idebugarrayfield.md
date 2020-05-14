---
title: IDebugArrayField Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField
helpviewer_keywords:
- IDebugArrayField interface
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dab01c1e956ced7e6894b951ab16f4ce68eb778b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736292"
---
# <a name="idebugarrayfield"></a>IDebugArrayField
Этот интерфейс описывает символ или тип массива.

## <a name="syntax"></a>Синтаксис

```
IDebugArrayField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует интерфейс [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Этот интерфейс представляет собой специализацию, представляющую объекты массива.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы получить этот интерфейс из интерфейса [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) вернет флаг. `FIELD_TYPE_ARRAY`

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсах [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) этот интерфейс реализует следующие:

|Метод|Описание|
|------------|-----------------|
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Возвращает количество элементов в массиве.|
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Получает тип элемента в массиве.|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Получает ранг массива.|

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
