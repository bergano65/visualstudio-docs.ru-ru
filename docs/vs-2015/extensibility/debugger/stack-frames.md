---
title: Кадры стека | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1efbc05528dd009098749fbe75316c0261b1b20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568473"
---
# <a name="stack-frames"></a>Кадры стека
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [кадров стека](https://docs.microsoft.com/visualstudio/extensibility/debugger/stack-frames).  
  
С точки зрения архитектуры отладчика **кадр стека**:  
  
-   — Это абстрактное представление стека, предоставляет контекст выполнения потока. Поток всегда выполняет внутри функции. Кадр стека содержит локальные переменные, функции и аргументы, к нему. Чтобы отладить с помощью Visual Studio, языка или среды, для которого выполняется отладка должна поддерживать кадры стека.  
  
-   Можно выявлять и описать сам себя и может возвращать соответствующего потока. Кадр стека может также возвращать контекст кода, который представляет текущего указателя инструкций, а также соответствующая документация и контекстов вычисления выражения.  
  
-   Имеет свойства, описывающие имя, тип и значение локальных переменных и аргументов, и которые отображаются в окнах отладки интегрированной среды разработки.  
  
-   Представленный [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, обычно создается с помощью модуля отладки (DE) или виртуальной машины, в результате выполнение потока.  
  
## <a name="see-also"></a>См. также  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)

