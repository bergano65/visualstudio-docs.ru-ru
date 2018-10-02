---
title: IDebugProperty2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c728c2e4955d35e2954fbda0a4a4432c550666d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571081"
---
# <a name="idebugproperty2"></a>IDebugProperty2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProperty2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2).  
  
Этот интерфейс представляет свойство кадра стека, свойство документа программы или некоторые другие свойства. Свойство обычно является результатом вычисления выражения.  
  
> [!NOTE]
>  Такое использование «свойства» не следует путать с, то есть переменную-член класса, несмотря на то что `IDebugProperty2` может представлять такая сущность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для представления определенного типа значения. Например значение может представлять числовое значение в результате вычисления выражения, контекста памяти, используемый для отображения в памяти, или список регистров и их значения.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) или [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) получить этот интерфейс, который представляет результат вычисления. `IDebugExpression2::EvaluateAsync` Возвращает этот интерфейс, отправляя [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) интерфейс SDM, который в свою очередь вызывает [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) требуется извлечь свойство.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) возвращает этот интерфейс для предоставления документа связанного скрипта.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) возвращает этот интерфейс, представляющий возвращаемое значение функции.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств программы, такие как имя или контекст памяти.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) возвращает этот интерфейс для представления различных свойств кадра стека, такие как локальные переменные.  
  
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
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

