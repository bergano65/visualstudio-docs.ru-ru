---
title: Точки останова (Visual Studio SDK) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739191"
---
# <a name="breakpoints-visual-studio-sdk"></a>Точки останова (пакет SDK для Visual Studio)
Существует три типа точек останова: ожидание, привязка и ошибка.

 **Ожидающая точка останова:**

- — Это абстракция, которая содержит все сведения, необходимые для привязки точки останова к одному или нескольким контекстам кода в одной или нескольких программах. Каждый раз, когда отлаживаемая программа вызывает загрузку кода, модуль отладки проверяет все ожидающие точки останова, чтобы определить, можно ли их привязать.

   Отложенная точка останова никогда не привязывается к коду, а собирает и, в свою очередь, содержит все связанные точки останова, которые она создает.

- Представляется интерфейсом [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Связанная точка останова:**

- Является абстракцией для точки останова, связанной с одним контекстом кода или привязанной к ней. Каждая связанная точка останова создается в ответ на ожидание точки останова. Однако ожидающая точка останова может создать более одной привязанной точки останова.

   При выгрузке кода связанная точка останова может быть отменена и отменена.

- Представляется интерфейсом [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Точка останова ошибки:**

- Является абстракцией для описания ошибки при попытке привязки ожидающей точки останова к контексту кода. Точка останова, описывающая ошибку в расположении или в выражении точки останова. Дополнительные сведения см. в разделе [Привязка точек останова](../../extensibility/debugger/binding-breakpoints.md).

   Ошибка в точке останова может быть либо ошибкой, либо предупреждением.

- Представляется интерфейсом [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>См. также раздел
- [Программы](../../extensibility/debugger/programs.md)
- [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
