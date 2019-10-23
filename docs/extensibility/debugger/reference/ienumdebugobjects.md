---
title: Иенумдебугобжектс | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 749b3faf938fbc862fdf9b406127c898ee6b6d98
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727563"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет коллекцию объектов, реализующих интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для предоставления наборов объектов, реализующих интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) . Обратите внимание, что это не стандартное перечисление COM из-за наличия метода [NOCOUNT](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
- Функция " [элементы](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) " возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Извлекает из перечисления следующий набор объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Пропускает указанное число записей.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Сбрасывает перечисление до первой записи.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Возвращает количество записей в перечислении.|

## <a name="remarks"></a>Заметки
 Этот интерфейс позволяет модулю отладки перечислять набор объектов в массиве.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft. VisualStudio. Debugger. Interop. dll

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)