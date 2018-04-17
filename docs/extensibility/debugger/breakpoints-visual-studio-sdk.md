---
title: Точки останова (SDK для Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42f2efe2785f508bedb104e495309ed40fc6ce39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="breakpoints-visual-studio-sdk"></a>Точки останова (SDK для Visual Studio)
Существует три вида точек останова: ожидание, границы и ошибки.  
  
 **В ожидании точки останова:**  
  
-   — Это абстракция, который содержит все сведения, необходимые для привязки точки останова для одного или нескольких контекстов кода в одну или несколько программ. Каждый раз, программа отлаживаемый код причины для загрузки, модуль отладки проверяет всех ожидающих точек останова, чтобы увидеть, если они привязаны.  
  
     Ожидающая точка останова сам никогда не привязывается к коду, но вместо собирает и говорят, что содержит всех связанных точек останова, которые он создает.  
  
-   Представленный [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейса.  
  
 **Связанная точка останова:**  
  
-   Связанная с абстракцию для точки останова или привязаны к контексту одного кода. Каждая связанная точка останова, формируется в ответ на ожидающая точка останова. Ожидающая точка останова, однако можно создавать несколько связанная точка останова.  
  
     При выгрузке кода связанная точка останова можно несвязанных и удалены.  
  
-   Представленный [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейса.  
  
 **Точки останова ошибок:**  
  
-   — Это абстракция для описания ошибки при попытке привязать контекст кода ожидающая точка останова. Точки останова по ошибке описывает либо ошибку в месте или на само выражение точки останова. Дополнительные сведения см. в разделе [привязка точки останова](../../extensibility/debugger/binding-breakpoints.md).  
  
     Ошибка точки останова может быть ошибка или предупреждение.  
  
-   Представленный [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)