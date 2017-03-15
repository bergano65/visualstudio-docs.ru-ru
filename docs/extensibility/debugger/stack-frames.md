---
title: "Кадры стека | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "кадры стека, отладка"
  - "отладка [пакет SDK для отладки], фреймов стека"
  - "кадры стека"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Кадры стека
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В терминах архитектуры отладчика, a **кадр стека**.  
  
-   Абстракция стека, предоставляющий контекст выполнения потока.  Поток всегда выполняется в рамках функции.  Кадр стека хранит локальные переменные и аргументы к нему.  Для отладки с Visual Studio, отлаживанными язык или среды должны поддерживать кадры стека.  
  
-   Позволяет и определения и описания и возвращает связанный поток.  Кадр стека может также возвращать контекст кода, который представляет текущий указатель инструкций, так же как и связанные контексты документации и оценки выражений.  
  
-   Содержит свойства, описывающие имя, тип и значение локальных переменных и аргументов, которые появляются в другой интегрированной среды разработки окна отладки.  
  
-   Представляет  [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) обычно интерфейс, созданный обработчиком отладки \(DE\) или виртуальной машиной вследствие выполнения потока.  
  
## См. также  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)