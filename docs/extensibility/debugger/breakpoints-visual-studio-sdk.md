---
title: "Точки останова (Visual Studio SDK) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fd0eccfa45f20217291b2e00eb175f8eac49d42d
ms.lasthandoff: 02/22/2017

---
# <a name="breakpoints-visual-studio-sdk"></a>Точки останова (SDK для Visual Studio)
Существует три типа точки останова: ожидание, привязки и ошибки.  
  
 **В ожидании точки останова:**  
  
-   — Это абстракция, который содержит все сведения, необходимые для привязки точки останова один или несколько контекстов код в одну или несколько программ. Каждый раз, программа отлаживаемый код причины для загрузки, отладчик проверяет всех ожидающих точек останова, чтобы увидеть, если они привязаны.  
  
     Ожидающая точка останова, сам никогда не привязывается к коду, но вместо собирает и называется для размещения всех связанных точек останова, которые он создает.  
  
-   Представлена [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейса.  
  
 **Связанная точка останова:**  
  
-   Связанные с абстракцию для точки останова или привязаны к контексту один код. Каждая связанная точка останова создается в ответ на ожидающая точка останова. Ожидающая точка останова, однако можно создавать несколько связанная точка останова.  
  
     При выгрузке кода связанная точка останова можно несвязанных и удаляются.  
  
-   Представлена [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейса.  
  
 **Точка останова ошибок:**  
  
-   Это абстракция для описания ошибки при попытке привязать ожидающая точка останова контекст кода. Точка останова ошибка описывает либо ошибку в месте или в само выражение точки останова. Дополнительные сведения см. в разделе [привязка точки останова](../../extensibility/debugger/binding-breakpoints.md).  
  
     Ошибка точки останова может быть ошибка или предупреждение.  
  
-   Представлена [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
