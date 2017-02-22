---
title: "Расширение модели объекта базового проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "объектная модель автоматизации, расширение"
  - "подтипы проектов, расширение модели объектов автоматизации"
  - "модель объектов автоматизации"
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Расширение модели объекта базового проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Подтип проекта может расширить объектной модели автоматизации базового проекта в следующих местах:  
  
-   Project.Extender («\< ProjectSubtypeName>») — это позволяет предложить объекта с помощью пользовательских методов подтипом проекта <xref:EnvDTE.Project>. Подтип проекта расширители автоматизации можно использовать для предоставления `Project` объекта.  <xref:EnvDTE80.IInternalExtenderProvider>интерфейс, реализованный агрегатора подтип основного проекта должно предлагать свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (соответствующий `itemid` значение VSITEMID_ROOT, из `VSITEMID`) CATID.  
  
-   ProjectItem.Extender («\< ProjectSubtypeName>») — это позволяет подтипом проекта предложить объекта с помощью пользовательских методов из определенного <xref:EnvDTE.ProjectItem> объект в рамках проекта. Подтип проекта можно использовать расширители автоматизации для предоставления этого объекта.  <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализованный агрегатора подтип основного проекта должен предлагать свой объект для `VSHPROPID_ExtObjectCATID` из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (соответствующий требуемой `VSITEMID`) CATID.  
  
-   Project.Properties — данная коллекция предоставляет независимым свойствам конфигурации `Project` объекта. Дополнительные сведения о свойствах проекта см. в разделе <xref:EnvDTE.Project.Properties%2A>. Подтип проекта можно использовать расширители автоматизации для добавления свойства в данную коллекцию.  <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализованный агрегатора подтип основного проекта должен предлагать свой объект для `VSHPROPID_BrowseObjectCATID` из VSHPROPID2 (соответствующий `itemid` значение VSITEMID_ROOT, от <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>) CATID.  
  
-   Configuration.Properties — это коллекция предоставляет зависимые свойства конфигурации проекта для определенной конфигурации (например, для отладки). Дополнительные сведения см. в разделах <xref:EnvDTE.Configuration>. Подтип проекта можно использовать расширители автоматизации для добавления свойства в данную коллекцию.  <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализованный агрегатора подтип основной проект предлагает его объект для CATID `VSHPROPID_CfgBrowseObjectCATID` (соответствующий `itemid` значение <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>).  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>интерфейс используется для различения одной конфигурации объекта от другого.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>