---
title: "Команда алгоритм маршрутизации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1463fe22d4b08933112ca1ad0cf28f38a4e102c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="command-routing-algorithm"></a>Алгоритм маршрутизации команд
В Visual Studio команды, обрабатываются ряд различных компонентов. Команды направляются из внутренней контекст, который основан на текущее выделение, самый внешний контекст (также известные как глобальные). Дополнительные сведения см. в разделе [доступности](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Порядок выполнения команды  
 Команды передаются через следующие уровни контекст командной строки:  
  
1.  Надстройки: Сначала предлагает команды для надстроек, присутствующие среды.  
  
2.  Приоритет команды: эти команды регистрируются с помощью метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Они вызываются для всех команд в Visual Studio и вызываются в порядке, в котором они были зарегистрированы.  
  
3.  Команды контекстного меню: сначала команду, расположенную в контекстном меню предлагается целевой объект команды, предоставляемая в контекстное меню и после этого типичные маршрутизации.  
  
4.  Набор целей команды панелей инструментов: эти целевые объекты команд регистрируются при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. `pCmdTarget` Параметр может быть `null`. Если это не `null`, то данный целевой объект команды используется для обновления все команды, расположенные на панели инструментов, вы настраиваете. Если оболочка — Настройка панели инструментов, то он передает фрейм окна, как `pCmdTarget` , чтобы все обновления для команд на вашей панели инструментов, проходят через рамки окна, даже если это не находится в фокусе.  
  
5.  Окно инструментов: Средства windows, которые обычно реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейсом, также должен реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс Visual Studio можно получить целевой объект команды, когда окно инструментов — это активное окно. Однако если окно инструментов, который имеет фокус, **проекта** окна, а затем команду направляется в <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс, который общий родительский объект для выбранных элементов. Если этот выбор распространяется на несколько проектов, команда направляется в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> иерархии. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Интерфейс содержит <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы, которые являются аналогом соответствующими командами в <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса.  
  
6.  Окно документа: Если команда имеет флаг RouteToDocs в vsct-файле, Visual Studio ищет цели команды на объект представления документа, который может иметь экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейса или экземпляра объекта документа (обычно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>интерфейс или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс). Если объект представления документа не поддерживает команду, Visual Studio направляет команду, чтобы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, который возвращается. (Это дополнительный интерфейс для объекта данных документа).  
  
7.  Текущей иерархии: текущей иерархии может быть проекта, которому принадлежит окно активного документа или иерархии, который выбран в **обозревателе решений**. Visual Studio ищет <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, реализованный на текущей или активных иерархии. Команды, которые являются допустимыми, каждый раз, когда иерархии активен, даже если фокус находится в окне документа элемент проекта должен поддерживать иерархия. Однако команды, которые применяются, только если **обозревателе решений** имеет фокус должен поддерживаться с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса и его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>методы.  
  
     **Вырезать**, **копирования**, **вставить**, **удаление**, **переименование**, **введите**и **По двойному щелчку** команды, требующие особых действий. Дополнительные сведения об обработке **удаление** и **удалить** команды в иерархиях см. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> интерфейса.  
  
8.  Global: Если команда не обрабатывается упомянутых ранее контекстах, Visual Studio пытается направить ее VSPackage, которому принадлежит команду, которая реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса. Если пакет VSPackage уже не загружены, он не загружен при Visual Studio вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. Загружаются только тогда, когда пакет VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызывается метод.  
  
## <a name="see-also"></a>См. также  
 [Конструктор команд](../../extensibility/internals/command-design.md)