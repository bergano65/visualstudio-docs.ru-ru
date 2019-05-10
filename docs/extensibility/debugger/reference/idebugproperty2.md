---
title: IDebugProperty2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f80d536e55241a92ed25738b6f8f444f11645b1
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457701"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Этот интерфейс представляет свойство кадра стека, свойство документа программы или некоторые другие свойства. Свойство обычно является результатом вычисления выражения.

> [!NOTE]
> Такое использование «свойства» не следует путать с, то есть переменную-член класса, несмотря на то что `IDebugProperty2` может представлять такая сущность.

## <a name="syntax"></a>Синтаксис

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс для представления определенного типа значения. Например значение может представлять числовое значение в результате вычисления выражения, контекста памяти, используемый для отображения в памяти, или список регистров и их значения.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) получить этот интерфейс, который представляет результат вычисления. `IDebugExpression2::EvaluateAsync` Возвращает этот интерфейс, отправляя [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейс SDM, который в свою очередь вызывает [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) требуется извлечь свойство.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) возвращает этот интерфейс для предоставления документа связанного скрипта.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) возвращает этот интерфейс, представляющий возвращаемое значение функции.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств программы, такие как имя или контекст памяти.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств кадра стека, такие как локальные переменные.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProperty2`.

|Метод|Описание|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Заполняет [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структура, описывающая свойства.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Задает значение свойства из строки.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Задает значение свойства из значения данной ссылки.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Перечисляет дочерние элементы свойства.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Возвращает родителя данного свойства.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Возвращает свойство, которое описывает свойство самого дальнего свойства.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Возвращает количество байтов памяти, из которых состоит значение свойства.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Возвращает контекст памяти для значения свойства.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Возвращает размер в байтах, значение свойства.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Возвращает ссылку на значение этого свойства.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Возвращает расширенные сведения свойства.|

## <a name="remarks"></a>Примечания
 Свойства, представленные как `IDebugProperty2` интерфейсом, может рассматриваться как значение с именем, типом и адрес. В более общие термины `IDebugProperty2` может представлять все, что имеет иерархическую структуру, с помощью родительских и дочерних узлов.

 Свойство обычно временная, которое существует только в течение текущего кадра стека, например. С другой стороны, ссылки, представленные как [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) интерфейс, срок действия которой составляет до тех пор, пока значение остается в памяти.

 Можно использовать в интегрированной среде разработки `IDebugProperty2` интерфейс, позволяющий пользователям просматривать и изменять свойства во время выполнения.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)