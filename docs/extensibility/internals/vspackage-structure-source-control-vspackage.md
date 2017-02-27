---
title: "Структура VSPackage (VSPackage управления источника) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Пакеты VSPackage, структура"
  - "пакеты управления исходным кодом, Обзор VSPackage"
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Структура VSPackage (VSPackage управления источника)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пакет SDK управления источника предоставляет рекомендации по созданию VSPackage, который позволяет разработчику элемента управления источника интегрировать свой функции системы управления версиями с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды. VSPackage — это компонент COM, обычно загружается по запросу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки \(IDE\) в зависимости от служб, объявленных для этого пакета в записи в реестр. Необходимо реализовать каждый VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. VSPackage обычно использует службы, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE и proffers некоторые службы.  
  
 VSPackage объявляет элементами меню и устанавливает состояние элемента по умолчанию через файла .vsct.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Интегрированной разработки отобразит пункты меню в этом состоянии до загрузки VSPackage. Впоследствии VSPackage реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения элементов меню.  
  
## Источник характеристик пакета управления  
 Система управления версиями VSPackage тесно интегрирована с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Семантика VSPackage включают:  
  
-   Интерфейс для реализации в силу выполняется VSPackage \( `IVsPackage` интерфейс\)  
  
-   Реализация пользовательского интерфейса команды \(файла .vsct и реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс\)  
  
-   Регистрация VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Системы управления версиями VSPackage должны взаимодействовать с этими других [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сущностей:  
  
-   Проекты  
  
-   Редакторы  
  
-   Решения  
  
-   Windows  
  
-   Выполнение таблицы document  
  
### Службы среды Visual Studio, который может быть использован  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Службы SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### VSIP интерфейсы реализованы и называется  
 Пакет управления версиями является VSPackage, и поэтому он может напрямую взаимодействовать с другими VSPackages, зарегистрированных с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Чтобы обеспечить полный спектр функции системы управления версиями, системы управления версиями VSPackage могут работать с интерфейсы, предоставляемые проектов или оболочки.  
  
 Каждый проект в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> распознается как проект в пределах [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Тем не менее, этот интерфейс не является специальным достаточно для системы управления версиями. Реализация управления проектов, которые должны быть под источником <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Этот интерфейс используется системой управления версиями VSPackage для запроса проект для его содержимое и предоставлять его глифы и данные привязки \(сведения, необходимые для установления соединения между расположение сервера и диска проекта, в системе управления версиями\).  
  
 Системы управления версиями, реализует VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, который в свою очередь позволяет проекта регистрируются для системы управления версиями и извлекать их состояние глифы.  
  
 Полный список интерфейсов, которые необходимо принимать во внимание VSPackage системы управления версиями см. в разделе [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## См. также  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)