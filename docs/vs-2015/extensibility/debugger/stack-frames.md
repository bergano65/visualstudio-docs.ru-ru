---
title: Кадры стека | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423391"
---
# <a name="stack-frames"></a>Кадры стека
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

С точки зрения архитектуры отладчика **кадр стека**:  
  
- — Это абстрактное представление стека, предоставляет контекст выполнения потока. Поток всегда выполняет внутри функции. Кадр стека содержит локальные переменные, функции и аргументы, к нему. Чтобы отладить с помощью Visual Studio, языка или среды, для которого выполняется отладка должна поддерживать кадры стека.  
  
- Можно выявлять и описать сам себя и может возвращать соответствующего потока. Кадр стека может также возвращать контекст кода, который представляет текущего указателя инструкций, а также соответствующая документация и контекстов вычисления выражения.  
  
- Имеет свойства, описывающие имя, тип и значение локальных переменных и аргументов, и которые отображаются в окнах отладки интегрированной среды разработки.  
  
- Представленный [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, обычно создается с помощью модуля отладки (DE) или виртуальной машины, в результате выполнение потока.  
  
## <a name="see-also"></a>См. также  
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Отладка ядра](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
