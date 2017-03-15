---
title: "Алгоритм маршрутизации команд | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Маршрутизация команд"
  - "маршрутизация команд"
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Алгоритм маршрутизации команд
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В Visual Studio команды, обрабатываются ряд различных компонентов. Команды направляются из внутренней контекст, который основан на текущее выделение, внешний контекст \(также известный как глобальное\). Дополнительные сведения см. в разделе [Доступность](../../extensibility/internals/command-availability.md).  
  
## Порядок выполнения команды  
 Команды, передаются следующие уровни контекст командной строки:  
  
1.  Надстройки: Сначала предлагает команду для надстройки, присутствующие среды.  
  
2.  Команды приоритет: эти команды зарегистрированы с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Они вызываются для каждой из команд в Visual Studio и вызываются в порядке, в котором они были зарегистрированы.  
  
3.  Команды контекстного меню: находятся в контекстном меню команду предлагается сначала целевой объект команды, предоставляемая в контекстное меню и после этого типичный маршрутизации.  
  
4.  Набор целей команды панелей инструментов: эти целевые объекты команд регистрируются при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>.`pCmdTarget` Параметр может быть `null`. Если это не `null`, то данный целевой объект команды используется для обновления любых команд на панели инструментов, вы настраиваете. Если оболочки, Настройка панели инструментов, а затем он передает фрейм окна, как `pCmdTarget` таким образом, чтобы все обновления для команды в потоке инструментов через фрейм окна, даже если он не находится в фокусе.  
  
5.  Окно средства: Средство windows, которые обычно реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, необходимо также реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс Visual Studio можно получить целевой объект команды, когда окно инструмента является активным окном. Тем не менее, если окно инструментов, имеет фокус находится **проекта** окна, а затем команду направляется <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейс, который является распространенным родительским объектом выбранных элементов. При выделении нескольких проектов, маршрутизируется команда <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> иерархии.<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Содержит интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> методы, которые являются аналогами для соответствующих команд на <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса.  
  
6.  Окно документа: Если команда имеет флаг RouteToDocs в виде файла .vsct, Visual Studio осуществляет поиск цели команды на объект представления документа, который может иметь экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейса или экземпляр объекта документа \(обычно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> интерфейс или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> интерфейс\). Если объект представления документа не поддерживает команды, Visual Studio направляет команды <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, который возвращается. \(Это необязательный интерфейс для объектов данных в документе\).  
  
7.  Текущая иерархия: текущей иерархии может быть проект, которому принадлежит окно активного документа или иерархии, который выбран в **обозревателе решений**. Visual Studio осуществляет поиск <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, реализованный в текущей или активным, иерархии. Иерархии, должны поддерживать команды, которые являются допустимыми, всякий раз, когда иерархии активен, даже если фокус находится на окне документа элемент проекта. Однако команды, которые применяются, только если **обозревателе решений** имеет фокус, которые должны поддерживаться с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> интерфейса и его <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>методы.  
  
     **Вырезать**, **копирования**, **Вставить**, **Удаление**, **Переименование**, **ВВОД**, и **по двойному** команд требуют специальной обработки. Дополнительные сведения об обработке **Удаление** и **Удаление** команды в иерархиях см. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> интерфейса.  
  
8.  Global: Если команда не обрабатываются упомянутых ранее контекстах, Visual Studio пытается его маршрутизировать VSPackage, который владеет команду, которая реализует <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса. Если VSPackage уже не загружены, он не загружается при Visual Studio вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод. VSPackage загружается только если <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> вызывается метод.  
  
## См. также  
 [Команды конструктора](../../extensibility/internals/command-design.md)