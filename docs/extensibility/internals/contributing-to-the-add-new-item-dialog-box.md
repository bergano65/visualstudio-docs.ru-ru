---
title: "Способствовали добавить новый элемент-диалоговое окно | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Добавить диалоговое окно «новый элемент», способствующих"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Способствовали добавить новый элемент-диалоговое окно
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Подтип проекта может предоставить полный каталог элементов **Добавление нового элемента** диалоговое окно " путем регистрации  **Добавить элемент** шаблоны под  `Projects` подраздел реестра.  
  
## Регистрация добавляет шаблоны нового элемента  
 Этот раздел находится вниз **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** в реестре.  Записи реестра ниже принимают a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект статистическая обработка вычислениеый постулативным подтипом данного проекта.  Запись [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект перечисляются ниже.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs` подраздел содержит записи реестра с путем к каталогу, в котором элементы, доступ в  **Добавление нового элемента** диалоговое окно " помещается.  
  
 Среда автоматически загружает все `AddItemTemplates` данные в группе  `Projects` подраздел реестра.  Это может включать данные для базовых реализации проекта, а также данные для типов, подтипа конкретного проекта.  Каждый подтип проекта определяется типом проекта `GUID`.  Подтип проекта может указать другой набор `Add Item` шаблоны должны использоваться для приправленного частностью экземпляра проекта путем поддержки  `VSHPROPID_ AddItemTemplatesGuid` перечисление от  <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> IN  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> реализация, чтобы возвратить значение идентификатора GUID подтипа проекта.  If `VSHPROPID_AddItemTemplatesGuid` используется свойство не задано, базовый GUID проекта.  
  
 Можно фильтровать элементы **Добавление нового элемента** диалоговое окно " путем реализации  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> интерфейс для объекта накопителя подтипа проекта.  Например, подтип проекта, который реализует проект базы данных путем статистического вычисления a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект может фильтровать  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] конкретные элементы  **Добавление нового элемента** диалоговое окно " путем фильтрации и, в свою очередь, может добавлять элементы проекта базы данных, определенные путем поддержки  `VSHPROPID_ AddItemTemplatesGuid` IN  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  Дополнительные сведения о фильтрации и добавления элементов в [Добавление элементов, чтобы добавить новый элемент диалоговые окна](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)диалоговое окно " см. в разделе  **Добавление нового элемента** .  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)