---
title: "Оценка стека вызова | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Отладка оценки стека вызовов [отладка SDK]"
  - "стеки вызовов, оценки"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Оценка стека вызова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Для просмотра стека вызовов кадры стека в режиме приостановки выполнения, необходимо реализовать [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) метод.  
  
## Методы оценки  
 Для простого обработчика отладки \(DE\), там может составление только один кадр стека.  Чтобы просмотреть кадр стека во время работы в режиме приостановки выполнения, необходимо реализовать следующие методы [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)|Возвращает контекст кода для кадра стека.  Контекст кода представляет текущий указатель инструкций в кадре стека.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст рисования для кадра стека.  Контекст рисования представляющий текущее расположение в исходном коде для кадра стека.  Требуется для просмотреть исходный код в тех случаях, когда останавливаются в программе.|  
  
 Эти методы требуют нескольких контекст\-родственных реализации интерфейсов и методов.  Таким образом, необходимо реализовать [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) метод и следующие методы  [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Получает диапазон выписки файла контекста документа.|  
  
 Чтобы перечислить контексты кода, необходимо реализовать все методы [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## См. также  
 [Управление выполнением и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)