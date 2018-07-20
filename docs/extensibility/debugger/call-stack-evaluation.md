---
title: Анализ стека вызова | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: f59ce938d2b37c5967856dc64c9116fa9a695dbe
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151438"
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