---
title: "Кадры стека | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2b225d84bfae6d182da86b2878a3761f67572be
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="stack-frames"></a>Кадры стека
С точки зрения архитектуры отладчик **кадр стека**:  
  
-   — Это абстракция стека, который предоставляет контекст выполнения потока. Поток всегда выполняет внутри функции. Он содержит локальные переменные, функции и аргументы кадр стека. Для отладки с помощью Visual Studio, языка или среды отлаживаемый должен поддерживать кадры стека.  
  
-   Можно выявлять и описывать себя и может возвращать соответствующего потока. Кадр стека может также возвращать контекст кода, который представляет текущего указателя инструкций, а также соответствующая документация и контекстов выражения вычисления.  
  
-   Содержит свойства, описывающие имя, тип и значения локальных переменных и аргументов, и которые отображаются в окнах отладки интегрированной среды разработки.  
  
-   Представленный [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, обычно создаются с помощью модуля отладки (DE) или виртуальной машины, в результате выполнение потока.  
  
## <a name="see-also"></a>См. также  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)