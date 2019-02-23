---
title: IDebugAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b9aba2be92516bab86f39eee55a3df4586eb09c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677972"
---
# <a name="idebugaddress"></a>IDebugAddress
Этот интерфейс представляет собой адрес элемента. Он возвращается с помощью обработчика символов.

## <a name="syntax"></a>Синтаксис

```
IDebugAddress : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Символ поставщик реализует этот интерфейс для представления адрес объекта.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Многие методы на многих интерфейсов возвращают этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Извлекает [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры, описывающий объект и его расположение.|

## <a name="remarks"></a>Примечания
 Поставщик символов возвращает этот интерфейс для представления объекта и его расположение в определенной области (например, функции, метода или класса). Этот интерфейс возвращается из и передать в различные методы поставщик символов и выражения средство оценки. Как правило поставщик символов является единственной сущностью, который должен интерпретировать содержимое этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)