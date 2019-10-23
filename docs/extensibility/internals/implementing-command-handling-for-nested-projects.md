---
title: Реализация обработки команд для вложенных проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727082"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Реализация обработки команд для вложенных проектов
Интегрированная среда разработки может передавать команды, передаваемые через <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>, и интерфейсы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> в вложенные проекты, а родительские проекты могут фильтровать или переопределять команды.

> [!NOTE]
> Фильтровать можно только команды, обычно обрабатываемые родительским проектом. Такие команды, как **Сборка** и **развертывание** , обрабатываемые интегрированной средой разработки, не могут быть отфильтрованы.

 Следующие шаги описывают процесс реализации обработки команд.

## <a name="procedures"></a>Процедуры

#### <a name="to-implement-command-handling"></a>Реализация обработки команд

1. Когда пользователь выбирает вложенный проект или узел во вложенном проекте:

   1. Интегрированная среда разработки вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>.

      Или...

   2. Если команда была создана в окне иерархии, например в команде контекстного меню в обозреватель решений, интегрированная среда разработки вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> в родительском проекте.

2. Родительский проект может проверять параметры, передаваемые в `QueryStatus`, такие как `pguidCmdGroup` и `prgCmds`, чтобы определить, должен ли родительский проект фильтровать команды. Если родительский проект реализуется для фильтрации команд, он должен задать:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Затем родительский проект должен возвращать `S_OK`.

    Если родительский проект не фильтрует команду, он должен просто возвращать `S_OK`. В этом случае интегрированная среда разработки автоматически направляет команду в дочерний проект.

    Родительский проект не должен маршрутизировать команду в дочерний проект. Интегрированная среда разработки выполняет эту задачу.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)