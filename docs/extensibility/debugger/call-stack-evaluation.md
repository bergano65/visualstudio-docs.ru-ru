---
title: Анализ стека вызова | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4d17c48f98a1f9bb0632df76ff5b04b0bdf5403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851226"
---
# <a name="call-stack-evaluation"></a>Анализ стека вызова
Чтобы просмотреть кадры стека из стека вызовов в режиме приостановки выполнения, необходимо реализовать [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) метод.  
  
## <a name="methods-for-evaluation"></a>Методы для оценки  
 Для простой отладки ядра (DE) может существовать только один кадр стека. Чтобы изучить кадр стека в режиме приостановки выполнения, необходимо реализовать следующие методы класса [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Возвращает контекст кода для кадра стека. Контекст кода представляет текущего указателя инструкций в кадре стека.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Получает контекст документа для кадра стека. Контекст документа представляет текущее расположение в исходном коде для кадра стека. Требуется для просмотра исходного кода, пока вы находитесь в программе.|  
  
 Эти методы требуют реализации нескольких связанных с контекстами интерфейсы и методы. Таким образом, необходимо реализовать [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) метод и следующих методов класса [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Получает диапазон файл инструкции к контексту документа.|  
  
 Для перечисления контекстов кода, необходимо реализовать все методы объекта [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>См. также  
 [Выполнение управления и состояние оценки](../../extensibility/debugger/execution-control-and-state-evaluation.md)