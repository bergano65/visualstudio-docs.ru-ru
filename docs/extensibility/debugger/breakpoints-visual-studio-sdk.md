---
title: Точки разрыва (Визуальная студия SDK) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739191"
---
# <a name="breakpoints-visual-studio-sdk"></a>Точки останова (пакет SDK для Visual Studio)
Существует три типа моментов разрыва: ожидающий, связанный и ошибочным.

 **Отложенная точка разрыва:**

- Является абстракцией, содержащей всю информацию, необходимую для привязки точки разрыва к одному или несколько контекстам кода в одной или нескольких программах. Каждый раз, когда отладка программы приводит к загрузке кода, отладка двигателя проверяет все ожидающие точки разрыва, чтобы увидеть, если они могут быть связаны.

   Сама точка разрыва никогда не связывается с кодом, а скорее собирает и, как говорят, содержит все связанные точки разрыва, которые она генерирует.

- Представлен интерфейсом [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Связанная точка разрыва:**

- Является абстракцией для точки разрыва, связанной с или связанной с одним контекстом кода. Каждая точка смывого генерируется в ответ на отложенную точку разрыва. Однако отложенная точка разрыва может генерировать несколько сытых точка разрыва.

   При разгрузке кода связанная точка разрыва может быть отбрасна и отброшена.

- Представлен интерфейсом [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Точка ошибки:**

- Является абстракцией для описания ошибки при попытке связать отложенную точку разрыва с контекстом кода. Точка ошибки описывает либо ошибку в местоположении, либо в самом выражении точки разрыва. Для получения дополнительной информации [см.](../../extensibility/debugger/binding-breakpoints.md)

   Ошибка точки разрыва может быть ошибкой или предупреждением.

- Представлен интерфейсом [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>См. также
- [Программы](../../extensibility/debugger/programs.md)
- [Концепции debugger](../../extensibility/debugger/debugger-concepts.md)
- [Контекст кода](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
