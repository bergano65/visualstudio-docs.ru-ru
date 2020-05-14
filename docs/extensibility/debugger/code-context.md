---
title: Контекст кода Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739152"
---
# <a name="code-context"></a>Контекст кода
При [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладке **контекст кода:**

- Обеспечивает абстракцию позиции в коде, известной движку отладки (DE). Для большинства архитектур времени выполнения сегодня контекст кода можно рассматривать как адрес в потоке инструкций программы. Для нетрадиционных языков, где код не может быть представлен инструкциями, контекст кода может быть представлен каким-то другими способами.

- Описывает текущее положение в потоке выполнения отладки программы.

- Существует только тогда, когда программа остановилась в точке разрыва.

- Имеет контекст связанного документа.

- Реализован интерфейсом [IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>См. также
- [Контекст документа](../../extensibility/debugger/document-context.md)
- [Контексты debugger](../../extensibility/debugger/debugger-contexts.md)
