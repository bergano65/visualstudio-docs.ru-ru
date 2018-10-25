---
title: Точки останова (пакет SDK для Visual Studio) | Документация Майкрософт
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
ms.openlocfilehash: 146c8c7e17017a675ad1077d03800328b0d345d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49932680"
---
# <a name="breakpoints-visual-studio-sdk"></a>Точки останова (пакет SDK для Visual Studio)
Существует три типа точек останова: ожидание "," граница "и" error.  
  
 **В ожидании точки останова:**  
  
- — Это абстракция, который содержит все сведения, необходимые для доступа к точке останова один или несколько контекстов кода в одну или несколько программ. Каждый раз, программа отлаживаемый код причины для загрузки, модуль отладки проверяет всех ожидающих точек останова, чтобы увидеть, если они могут быть привязаны.  
  
   Ожидающая точка останова, сам никогда не привязывается к коду, но вместо собирает и говорят, что для хранения всех связанных точек останова, которые он создает.  
  
- Представленный [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) интерфейс.  
  
  **Связанная точка останова:**  
  
- Связанные с абстракцию для точки останова или привязаны к контексту единый код. Каждая связанная точка останова формируется в ответ на точку останова. Ожидающая точка останова, однако, можно создавать более одного связанная точка останова.  
  
   При выгрузке кода связанная точка останова можно несвязанных и удалены.  
  
- Представленный [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) интерфейс.  
  
  **Ошибка точки останова:**  
  
- — Это абстракция для описания ошибки при попытке привязать ожидающая точка останова контекста кода. Точки останова ошибка описывает либо ошибку в расположении или самого выражения точка останова. Дополнительные сведения см. в разделе [привязка точки останова](../../extensibility/debugger/binding-breakpoints.md).  
  
   Ошибка точки останова может быть ошибка или предупреждение.  
  
- Представленный [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Программы](../../extensibility/debugger/programs.md)   
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)   
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)