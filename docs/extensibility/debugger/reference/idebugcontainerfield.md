---
title: IDebugContainerField (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72296517a64c6dcfcb8e347fb00588504aa75a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733219"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Этот интерфейс представляет собой символ или тип, который является контейнером для других символов или типов.

## <a name="syntax"></a>Синтаксис

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует интерфейс [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Этот интерфейс также является базовым классом для всех интерфейсов, представляющих контейнеры.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Многие методы на многих интерфейсах возвращают этот интерфейс. Поскольку это базовый класс для всех контейнеров, более специализированные интерфейсы могут быть получены из этого интерфейса с помощью [queryInterface.](/cpp/atl/queryinterface) Такие интерфейсы включают [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), и [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсе [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Создает регистратор для полей контейнера.|

## <a name="remarks"></a>Примечания
 Массивы (контейнеры для переменных), классы (контейнеры для методов и переменных) и методы (контейнеры для параметров и локальных переменных) являются примерами контейнеров.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
