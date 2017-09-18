---
title: "Редактор фабрик | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - редактор фабрик"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Редактор фабрик
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Фабрика редактора создает объекты редактора и помещает их в границы окна, известную как физическое представление.  Он создает объекты представления данных документа и документ, необходимые для создания редакторы и конструкторы.  Необходимые для создания фабрики редактора редактор Visual Studio и любой основной стандартный редактор.  Специализированный редактор также при необходимости можно создать с фабрикой редактора.  
  
 Создать фабрику редактора, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.  В следующем примере показано, как реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> создать фабрику редактора.  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Редактор загружается при первом открытии файла, тип обрабатывается этим редактором.  Можно выбрать, чтобы открыть или конкретным редактор или редактор по умолчанию.  Если выбрать редактор по умолчанию, интегрированная среда разработки \(ide\) определяет нужный редактор, чтобы открыть, а затем открыть его.  Дополнительные сведения см. в разделе [Определение редактора откроется файл в проекте](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## Регистрация фабрики редактора  
 Прежде чем использовать редактор, который был создан, необходимо зарегистрировать сведения о нем, включая расширение файла, оно может обработать.  
  
 Если в VSPackage написаны в управляемом коде, можно использовать управляемый метод .NET Framework пакета \(MPF\) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> регистрация фабрики редактора, установленном после загрузки VSPackage.  Если в VSPackage записывается в неуправляемом коде, необходимо зарегистрировать пользовательское производство с помощью редактора <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> служба.  
  
### Регистрация фабрики редактора с помощью управляемого кода  
 Необходимо зарегистрировать в фабрику редактора в VSPackage `Initialize` метод.  Первый вызов `base.Initialize`, а затем вызовите  <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> для каждого фабрики редактора  
  
 В управляемом коде никакого регистрацию необходимости фабрика редактора, поскольку VSPackage обрабатывающий это автоматически.  Кроме того, если фабрику редактора реализует <xref:System.IDisposable>автоматически удален при его регистрации.  
  
### Регистрация фабрики редактора с помощью неуправляемого кода  
 в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализация для пакета редактора, использующий  `QueryService` метод, вызываемый  `SVsRegisterEditors`.  Это возвращает указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> метод, передавая пользовательскую реализацию  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> интерфейс.  Вы mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> в отдельном классе.  
  
## Процесс регистрации фабрики редактора  
 Следующий процесс происходит, когда Visual Studio загружает редактор с помощью работы фабрика редактора.  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>система проекта вызывает  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
2.  Этот метод возвращает фабрику редактора.  Visual Studio задерживает загрузку пакета редактора, однако до системы проектов в действительности не будут требуется редактор.  
  
3.  При необходимости вызывает редактор системе проектов Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, специализированный метод, возвращающий оба представления документа и объекты данных документа.  
  
4.  Если вызовы Visual Studio в рабочей среде с помощью редактора <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> возврат и объект данных документа и объект представления документа Visual Studio, а затем создает окно документа, устанавливает объект представления документа в нем, и делает запись в выполняющуюся document table \(RDT\) для объекта данных документа.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Таблицы запущенных документа](../extensibility/internals/running-document-table.md)