---
title: IEnumDebugОбъекты Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c04409fb695613fea5d54b285946c04719fbe5b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716263"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс представляет собой набор объектов, реализующих интерфейс [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

## <a name="syntax"></a>Синтаксис

```
IEnumDebugObjects : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс, чтобы предоставить наборы объектов, реализующих интерфейс [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md) Обратите внимание, что это не стандартный пересчет COM из-за присутствия метода [GetCount.](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Извлекает следующий набор объектов [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) из перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Пропускает определенное количество записей.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Сброс исчисляется перечислением первой записи.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md) (Клонировать)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Извлекает количество записей в перечислении.|

## <a name="remarks"></a>Примечания
 Этот интерфейс позволяет движку отладки перечислить над набором объектов в массиве.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
