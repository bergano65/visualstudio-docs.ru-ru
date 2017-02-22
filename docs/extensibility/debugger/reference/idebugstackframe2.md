---
title: "IDebugStackFrame2 | Microsoft Docs"
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
  - "IDebugStackFrame2"
helpviewer_keywords: 
  - "Интерфейс IDebugStackFrame2"
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет один стек при вызове кадра стека в указанном потоке.  
  
## Синтаксис  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, представляющий кадр стека.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) восстановление  [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс.  Вызов [Далее](../Topic/IEnumDebugFrameInfo2::Next.md) получение a  [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структура, содержащая  `IDebugStackFrame2` интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugStackFrame2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|Возвращает контекст кода для данного кадра стека.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст рисования для этого кадра стека.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Возвращает имя кадра стека.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Возвращает описание кадра стека.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Возвращает представление компьютер\-зависимой ячейки диапазона физических адресов, связанных с кадром стека.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Возвращает контекст вычисления для оценки выражений внутри текущего контекста кадра стека и потока.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Возвращает язык, связанный с кадром стека.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Возвращает описание свойств, связанных с кадром стека.|  
|[EnumProperties](../Topic/IDebugStackFrame2::EnumProperties.md)|Создает перечислитель для свойств кадра стека.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Получает поток, связанный с кадром стека.|  
  
## Заметки  
 Этот интерфейс получен только тогда, когда была остановлена отлаживаемой программы в точке останова \(или вызвано точкой останова пользователь\-набора или множеств\).  От этого интерфейса, можно получить контекст выражения для вычисления выражения, список регистров, могут быть возвращены или стек вызовов можно получить и проверки.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)