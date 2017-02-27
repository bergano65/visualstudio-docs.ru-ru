---
title: "IEnumDebugThreads2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2"
helpviewer_keywords: 
  - "IEnumDebugThreads2"
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugThreads2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Это interfac перечисляет потоки, работающие в течение сеанса отладки.  
  
## Синтаксис  
  
```  
IEnumDebugThreads2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представлять список потоков в программе.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) получить этот интерфейс, представляющий список всех потоков во все программы, работающие в процессе.  Вызов [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) получить этот интерфейс, представляющий список потоков, работающих в программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugThreads2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../Topic/IEnumDebugThreads2::Next.md)|Извлекает заданное количество потоков в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Пропустить указанное количество потоков в последовательности перечисления.|  
|[Сбросить](../Topic/IEnumDebugThreads2::Reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий.|  
|[GetCount](../Topic/IEnumDebugThreads2::GetCount.md)|Получает количество потоков в перечислителе.|  
  
## Заметки  
 Visual Studio обычно получает этот интерфейс, чтобы обновить **потоки** окно так же, как получить первый поток списка, чтобы вызвать  [Выполнение](../../../extensibility/debugger/reference/idebugprocess3-execute.md)"  [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)и  [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md).  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)   
 [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)   
 [Выполнение](../../../extensibility/debugger/reference/idebugprocess3-execute.md)