---
title: Вычисление стека вызовов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146404"
---
# <a name="call-stack-evaluation"></a>Анализ стека вызова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы просмотреть кадры стека стека вызовов в режиме приостановки выполнения, необходимо реализовать метод [енумфрамеинфо](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .  
  
## <a name="methods-for-evaluation"></a>Методы для оценки  
 Для простого модуля отладки (DE) может существовать только один кадр стека. Чтобы изучить кадр стека в режиме приостановки выполнения, необходимо реализовать следующие методы [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Возвращает контекст кода для кадра стека. Контекст кода представляет текущий указатель инструкции в кадре стека.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст документа для кадра стека. Контекст документа представляет текущее расположение в исходном коде для кадра стека. Требуется для просмотра исходного кода при остановке в программе.|  
  
 Для этих методов требуется реализация нескольких интерфейсов и методов, связанных с контекстом. Поэтому необходимо реализовать метод [жетдокументконтекст](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) и следующие методы [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Возвращает диапазон инструкций File в контексте документа.|  
  
 Чтобы перечислить контексты кода, необходимо реализовать все методы [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>См. также:  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
