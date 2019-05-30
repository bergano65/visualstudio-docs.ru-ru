---
title: IDebugContainerField | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d633b7e42f8c7f64a818539694837b954ea31e72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332517"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Этот интерфейс представляет символ или тип, который является контейнером для других символов или типов.

## <a name="syntax"></a>Синтаксис

```
IDebugContainerField : IDebugField
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс на тот же объект, реализующий [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс. Этот интерфейс также является базовым классом для всех интерфейсов, представляющих контейнеры.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Многие методы на многих интерфейсов возвращают этот интерфейс. Так как это базовый класс для всех контейнеров, из этого интерфейса можно получить более специализированных интерфейсов, с помощью [QueryInterface](/cpp/atl/queryinterface). Такие интерфейсы включают [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), и [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Создает перечислитель для полей контейнера.|

## <a name="remarks"></a>Примечания
 Массивы (контейнеры для переменных), классы (содержащих методы и переменные) и методы (содержащих параметры и локальные переменные) являются примерами контейнеров.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)