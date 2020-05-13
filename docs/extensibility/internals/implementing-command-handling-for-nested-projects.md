---
title: Реализация командной обработки для nested проектов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707598"
---
# <a name="implementing-command-handling-for-nested-projects"></a>Реализация обработки команд для вложенных проектов
IDE может передавать команды, которые <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> передаются <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> через и интерфейсы вложенных проектов, или родительские проекты могут фильтровать или переопределять команды.

> [!NOTE]
> Отфильтровывать можно только команды, обычно обрабатываемые родительским проектом. Команды, такие как **сборка** и **развертывание,** обрабатываемые IDE, не могут быть отфильтрованы.

 Следующие шаги описывают процесс реализации обработки команд.

## <a name="procedures"></a>Процедуры

#### <a name="to-implement-command-handling"></a>Реализация обработки команд

1. Когда пользователь выбирает вложенный проект или узло в вложенном проекте:

   1. IDE вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод.

      — или —

   2. Если команда возникла в окне иерархии, например в команде меню ярлыка <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> в Solution Explorer, IDE вызывает метод на родительских элементах проекта.

2. Родительский проект может изучить `QueryStatus`параметры, которые `pguidCmdGroup` `prgCmds`должны быть переданы, например, и, чтобы определить, должен ли родительский проект фильтровать команды. Если родительский проект реализован для фильтрации команд, он должен установить:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Затем родительский проект `S_OK`должен вернуться.

    Если родительский проект не фильтрует команду, `S_OK`он должен просто вернуться. В этом случае IDE автоматически направляет команду в проект «ребенок».

    Родительский проект не должен направлять команду в проект «ребенок». IDE выполняет эту задачу.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Проекты вложения](../../extensibility/internals/nesting-projects.md)
