---
title: "IDebugProperty2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2"
helpviewer_keywords: 
  - "Интерфейс IDebugProperty2"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет свойство кадра стека, свойство документа программы или другое свойство.  Свойство обычно является результатом оценки выражений.  
  
> [!NOTE]
>  Эта использование "свойства" не следует путать с этой переменной члена класса, хотя смыслью `IDebugProperty2` может представлять ту сущность.  
  
## Синтаксис  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, представляющий заданный тип значения.  Например, значение может быть по числовому значением в результате оценки выражений, контекст памяти, используемого для отображения памяти или списка регистров и их значений.  
  
## Замечания для вызывающих объектов  
 Вызов [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) OR  [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) получить этот интерфейс, представляющий результат вычисления.  `IDebugExpression2::EvaluateAsync` возвращает этот интерфейс, отправляя  [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейс SDM, которое, в свою очередь, вызывает  [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) извлечь свойство.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) возвращает этот интерфейс, чтобы предоставить связанный документ скрипта.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) возвращает этот интерфейс для представления возвращаемое значение функции.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств, как имя программы, либо контекст памяти.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств кадра стека как локальные переменные.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProperty2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Заполняет a [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) структура, описывающая свойства.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Устанавливает значения свойства из строки.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Устанавливает значения свойства из значений заданного ссылки.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Перечисляет дочерние элементы свойства.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Возвращает родительский объект свойства.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Возвращает свойство, которое описывает несколько всего\-выведенное свойство свойства.|  
|[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)|Возвращает количество байтов памяти, составляющих значение свойства.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Возвращает контекст памяти для значения свойства.|  
|[GetSize](../Topic/IDebugProperty2::GetSize.md)|Возвращает размер \(в байтах\) значения свойства.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Возвращает ссылку на эту значения свойства.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Возвращает подробные сведения свойства.|  
  
## Заметки  
 Свойство, представленное `IDebugProperty2` интерфейс, может рассматриваться как значения с именем, типом и адресом.  в более общие термины, `IDebugProperty2` может представлять что\-либо, который имеет иерархическую структуру, с родительскиями и дочерними узлами.  
  
 Свойство обычно транзиторно, продолжающ только при условии, что текущий кадр стека, например.  С другой стороны, ссылка на [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) интерфейс, последние если значение остается в памяти.  
  
 Интегрированная среда разработки может использовать `IDebugProperty2` интерфейс, чтобы позволить пользователям просмотр и изменение свойств во время выполнения.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)