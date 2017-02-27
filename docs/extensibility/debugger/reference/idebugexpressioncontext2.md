---
title: "IDebugExpressionContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "Интерфейс IDebugExpressionContext2"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет контекст для оценки выражений  
  
## Синтаксис  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представлять контекст, в котором выражение можно вычислить.  
  
## Замечания для вызывающих объектов  
 Вызов [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает данный интерфейс.  Этот интерфейс доступен, только если была приостановлена отлаживаемой программы и кадр стека доступен.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugExpressionContext2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetName](../Topic/IDebugExpressionContext2::GetName.md)|Извлекает имя контекста оценки.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Анализирует выражение на основе текста для оценки.|  
  
## Заметки  
 Контекст выполнения можно представить в виде областей для выполнения оценки выражений.  
  
 Когда программа останавливала сеанс отладки \(SDM\) получает диспетчер кадр стека, вызвав из DE [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  SDM затем вызывает метод [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) доступ  `IDebugExpressionContext2` интерфейс.  Это за вызовом [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) создание  [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, представляющий проанализированное выражение готовности быть вычисляемым.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)