---
title: "Практическое руководство: Откройте стандартные редакторы | Microsoft Docs"
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
  - "редакторы [Visual Studio SDK], открытие"
  - "открытие редакторов стандартные проекты [Visual Studio SDK]"
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: Откройте стандартные редакторы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При открытии стандартный редактор можно позволить интегрированной среде разработки задавать стандартный редактор, определенный тип файла, вместо указания редактора проектов для файла.  
  
 Выполните следующую процедуру для реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> метод.  Это открытии файла проекта в стандартном редакторе.  
  
### Реализация метода OpenItem со стандартным редактором  
  
1.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> \(`RDT_EditLock`\) определить, является ли объектный файл объекта данных документа уже открыт.  
  
2.  Если файл уже открыт, то resurface файл, вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> метод, указывая значение  `IDO_ActivateIfOpen` для  `grfIDO` параметр.  
  
     Если файл открыт и документ принадлежит другим проектом, чем при вызове проект, проект возвращает предупреждение, открываемый в редакторе из другого проекта.  Окно файла затем отображается.  
  
3.  Если документ не открыт или не в таблице текущих документов, вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> \(метод`OSE_ChooseBestStdEditor`стандартный\) откройте редактор для файла.  
  
     При вызове метода интегрированная среда разработки выполняет следующие задачи:  
  
    1.  Интегрированная среда разработки просматривает подраздел редакторов} {guidEditorType \/Extensions в реестре, чтобы определить, который редактор может открыть файл и имеет наивысший приоритет, позволяющий сделать это.  
  
    2.  После того как интегрированная среда разработки определяла, который редактор может открыть файл, интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  Реализация редактора этого метода возвращает сведения, необходимые для интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> вновь открыт документ и сайт.  
  
    3.  Наконец, интегрированная среда разработки загружает документ с помощью обычного интерфейса сохраняемости, например <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Если интегрированная среда разработки ранее определяла, что иерархия или элемент иерархии доступны вызовы интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> метод в проекте получить контекст уровня проекта  <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> указатель, который требуется возвратить с  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> вызов метода.  
  
4.  Return <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> указатель в интегрированной среде разработки при вызове интегрированной среды разработки  <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> в проекте, если нужно разрешить редактор получить контекст из проекта.  
  
     Чтобы выполнить этот шаг позволяет службам предложения проекта дополнительным в редактор.  
  
     Если объект представления документа или представления документа был успешно будет помещен в рамку окна, объект инициализирован со своими данными путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## См. также  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Открытие и сохранение элементов проекта](../extensibility/internals/opening-and-saving-project-items.md)   
 [Практическое руководство: открытие редакторов конкретного проекта](../extensibility/how-to-open-project-specific-editors.md)   
 [Практическое руководство: открытие редакторов для открытых документов](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Отображение файлов с помощью команды Открыть файл](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)