---
title: Кадры стека | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35b22c47aa80713ae494f868996142e776c94a0a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020341"
---
# <a name="stack-frames"></a>Кадры стека
В архитектуре отладчик *кадр стека*:  
  
-   — Это абстрактное представление стека, предоставляет контекст выполнения потока. Поток всегда выполняет внутри функции. Кадр стека содержит локальные переменные, функции и аргументы, к нему. Чтобы отладить с помощью Visual Studio, языка или среды, для которого выполняется отладка должна поддерживать кадры стека.  
  
-   Можно выявлять и описать сам себя и может возвращать соответствующего потока. Кадр стека может также возвращать контекст кода, который представляет текущего указателя инструкций и связанную документацию и контекстов вычисления выражения.  
  
-   Имеет свойства, описывающие имя, тип и значение локальных переменных и аргументов, и которые отображаются в окнах отладки интегрированной среды разработки.  
  
-   Представленный [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, обычно создается с помощью модуля отладки (DE) или виртуальной машины, в результате выполнение потока.  
  
## <a name="see-also"></a>См. также  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)