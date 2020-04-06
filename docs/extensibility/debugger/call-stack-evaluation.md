---
title: Оценка стеков вызова (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739174"
---
# <a name="call-stack-evaluation"></a>Оценка стека вызова
Для просмотра кадров стека вызовов во время перерыва необходимо реализовать метод [EnumFrameInfo.](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="methods-for-evaluation"></a>Методы оценки
 Для простого движка отладки (DE) может быть только один стек кадр. Чтобы изучить кадр стека во время перерыва, необходимо реализовать следующие методы [IDebugStackFrame2.](../../extensibility/debugger/reference/idebugstackframe2.md)

|Метод|Описание|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Получает контекст кода для кадра стека. Контекст кода представляет текущую инструкцию в кадре стека.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Получает контекст документа для кадра стека. Контекст документа представляет текущее местоположение в исходном коде для кадра стека. Требуется для просмотра исходного кода, когда вы остановились в программе.|

 Эти методы требуют реализации нескольких контекстных интерфейсов и методов. Таким образом, необходимо реализовать метод [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) и следующие методы [IDebugDocumentContext2.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

|Метод|Описание|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Получает диапазон контекста файла заявления контекста документа.|

 Чтобы перечислить контексты кода, необходимо реализовать все методы [IEnumDebugCodeContexts2.](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

## <a name="see-also"></a>См. также
- [Контроль исполнения и государственная оценка](../../extensibility/debugger/execution-control-and-state-evaluation.md)
