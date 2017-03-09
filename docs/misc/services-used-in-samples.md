---
title: "Службы, используемые в примерах | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы, отображающиеся в примерах"
  - "примеры, службы"
ms.assetid: 04864feb-9b8b-45c4-8233-fc2ed9273987
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Службы, используемые в примерах
Примеры, включенные в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] используйте несколько служб.  В следующем списке показаны некоторые часто используемых служб и образцы, которые их используют.  
  
> [!NOTE]
>  Если ссылка и неподдерживаемые образцы доступны только пример ссылки указана.  
  
|Служба|Пример|  
|------------|------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry>|BscEdit, ProjectSubtype|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>|[Практическое руководство: использование журнала действий](../extensibility/how-to-use-the-activity-log.md)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddProjectItemDlg>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>|BscPrj|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChange>|Устаревший.  Взамен рекомендуется использовать <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>|Пример Reference.HelpIntegration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Пример SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>|Пример SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsResourceManager>|Reference.Package, Reference.ToolWindow и множество других образцов|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Пример SingleViewEditor.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Reference.Package, Reference.ToolWindow и множество других образцов|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|BscEdt, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>|SingleViewEditor, BscPrj, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Reference.ToolWindow, BscEdit и множество других образцов|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|BscEdit, FigPkg|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsWindowFrame>|Reference.ToolWindow|  
  
## См. также  
 [Список доступных служб](../extensibility/internals/list-of-available-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)