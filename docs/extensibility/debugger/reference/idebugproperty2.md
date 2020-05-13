---
title: IDebugProperty2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721221"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Этот интерфейс представляет свойство кадра стека, свойство документа программы или другое свойство. Свойство обычно является результатом оценки выражения.

> [!NOTE]
> Такое использование "имущества" не следует путать с тем, что `IDebugProperty2` означает переменную члена класса, хотя может представлять такую сущность.

## <a name="syntax"></a>Синтаксис

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс, чтобы представлять определенный вид значения. Например, значение может быть числовым значением в результате оценки выражения, контекстом памяти, используемым для отображения памяти, или списком регистров и их значений.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Call [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync,](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) чтобы получить этот интерфейс, который представляет собой результат оценки. `IDebugExpression2::EvaluateAsync`возвращает этот интерфейс, отправив интерфейс [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) в SDM, который, в свою очередь, вызывает [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) для получения свойства.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) возвращает этот интерфейс, чтобы предоставить связанный документ скрипта.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) возвращает этот интерфейс, чтобы представить значение возврата функции.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств программы, таких как имя или контекст памяти.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств кадра стека, таких как локальные переменные.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProperty2`.

|Метод|Описание|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Заполняет [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структуру, описывая свойство.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Устанавливает значение свойства из строки.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Устанавливает значение свойства от значения данной ссылки.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Перечисляет детей собственности.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Возвращает родитель свойства.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Возвращает свойство, описывая наиболее полученное свойство свойства.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Возвращает байты памяти, которые составляют значение свойства.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Возвращает контекст памяти для значения свойства.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Возвращает размер, в байтах, стоимости свойства.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Возвращает ссылку на стоимость этого свойства.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Возвращает расширенную информацию о собственности.|

## <a name="remarks"></a>Примечания
 Свойство, представленное `IDebugProperty2` интерфейсом, можно рассматривать как значение с именем, типом и адресом. В более общих `IDebugProperty2` терминах, может представлять все, что имеет иерархическую структуру, с родителями и детскими узлами.

 Свойство, как правило, временное, длится только до тех пор, как текущий кадр стека, например. С другой стороны, ссылка, представленная интерфейсом [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) длится до тех пор, пока значение остается в памяти.

 IDE может использовать `IDebugProperty2` интерфейс, чтобы позволить пользователям просматривать и изменять свойства во время выполнения.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
