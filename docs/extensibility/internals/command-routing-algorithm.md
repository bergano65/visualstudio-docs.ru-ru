---
title: Алгоритм командной ракруты (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709538"
---
# <a name="command-routing-algorithm"></a>Алгоритм командной разработки
В Visual Studio команды обрабатываются несколькими различными компонентами. Команды направляются из внутреннего контекста, который основан на текущем выборе, во внешний (также известный как глобальный) контекст. Для получения дополнительной [информации](../../extensibility/internals/command-availability.md)см.

## <a name="order-of-command-resolution"></a>Разрешение командования
 Команды передаются через следующие уровни контекста командования:

1. Дополнительные предложения: Среда сначала предлагает команду для любых надсмов, которые присутствуют.

2. Приоритетные команды: Эти команды регистрируются с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Они вызваны для каждой команды в Visual Studio, и называются в порядке, в котором они были зарегистрированы.

3. Команды меню контекста: Команда, расположенная в контекстном меню, сначала предлагается цели команды, которая предоставляется в меню контекста, а затем типичной реукторе.

4. Панель инструментов устанавливает командные цели: эти <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>командные цели регистрируются при вызове. Параметр `pCmdTarget` может `null`быть . Если это `null`не так, то эта цель команды используется для обновления любых команд, расположенных на панели инструментов, которые вы настраиваете. Если оболочка настраивает панель инструментов, то она `pCmdTarget` проходит оконную раму так, чтобы все обновления команд на панели инструментов протекают через оконную раму, даже если она не находится в фокусе.

5. Окно инструмента: окна инструментов, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> которые обычно реализуют интерфейс, также должны реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, чтобы Visual Studio мог получить цель команды, когда окно инструмента является активным окном. Однако, если окно инструмента, в котором фокус фокусируется, является <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> окном **Project,** то команда направляется в интерфейс, который является общим родителем выбранных элементов. Если этот выбор охватывает несколько проектов, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> команда направляется в иерархию. Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> содержит <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы, аналогичные соответствующим командам на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейсе.

6. Окно документа: Если в `RouteToDocs` файле *.vsct* у команды есть флаг, Visual Studio ищет цель команды на <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> объекте представления документа, которая является <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> либо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> экземпляром интерфейса, либо экземпляром объекта документа (обычно интерфейсом или интерфейсом). Если объект представления документа не поддерживает команду, Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> направляет команду к возвращенному интерфейсу. (Это дополнительный интерфейс для объектов данных документов.)

7. Текущая иерархия: Текущая иерархия может быть проектом, владеющим действующим окном документа или иерархией, выбранной в **Solution Explorer.** Visual Studio ищет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, который реализован в текущей или активной иерархии. Иерархия должна поддерживать команды, действительные всякий раз, когда иерархия активна, даже если в центре внимания находится оконное окно документа элемента проекта. Тем не менее, команды, которые применяются только тогда, когда <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> **Solution Explorer** имеет фокус должен быть поддержан с помощью интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> и его методов.

     **Вырезать**, **Копировать**, **Вставить**, **Удалить**, **переименовать**, **Введите**, и **DoubleClick** команды требуют специальной обработки. Для получения информации о том, как обрабатывать команды <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> **Удаления** и **удаления** в иерархиях, см.

8. Глобальный: Если команда не была обработана ранее упомянутыми контекстами, Visual Studio пытается направить ее в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> VSPackage, который владеет командой, которая реализует интерфейс. Если VSPackage уже не загружен, он не загружается, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> когда Visual Studio вызывает метод. VSPackage загружается только <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> тогда, когда метод вызывается.

## <a name="see-also"></a>См. также
- [Командный дизайн](../../extensibility/internals/command-design.md)
