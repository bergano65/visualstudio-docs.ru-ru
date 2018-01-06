---
title: "Дополнение добавить новый элемент-диалоговое окно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 923d95256a3ab0e63bdcf35c7ae38d70a117fa02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Дополнение добавить новый элемент-диалоговое окно
Подтип проекта может предоставить полный новый каталог элементов для **Добавление нового элемента** диалоговое окно, зарегистрировав **добавить элемент** шаблоны по `Projects` подраздел реестра.  
  
## <a name="registering-add-new-item-templates"></a>Регистрация добавить новый элемент шаблонов  
 В этом разделе находится в папке **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** в реестре. Предположим, параметрами реестра [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, упорядоченные по подтип гипотетической проекта. Записи для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, перечислены ниже.  
  
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
  
 `AddItemTemplates\TemplateDirs` Подраздел содержит записи реестра с путем к каталогу, где элементы становятся доступными в **Добавление нового элемента** помещаются диалоговое окно.  
  
 Среде автоматически загружает все `AddItemTemplates` данных в группе `Projects` подраздел реестра. Это могут быть данные для реализации базового проекта, а также данные для конкретных подтипов типов проектов. Каждый проект подтип определяется по типу проекта `GUID`. Подтип проекта можно указать, альтернативный набор `Add Item` следует использовать шаблоны для конкретного проекта интерфейсам экземпляра с помощью поддержки `VSHPROPID_ AddItemTemplatesGuid` перечисления из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> реализацию, чтобы вернуть идентификатор GUID значение подтип проекта. Если `VSHPROPID_AddItemTemplatesGuid` свойство не задано, используется GUID базового проекта.  
  
 Можно отфильтровать элементы в **Добавление нового элемента** диалоговое окно, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> интерфейс объекта агрегатора подтип проекта. Например, подтип проекта, реализующий проект базы данных, применяя статистическую обработку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, можно отфильтровать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы из **Добавление нового элемента** диалоговое окно путем реализации фильтрации и включить, можно добавить определенные элементы проекта базы данных, поддерживая `VSHPROPID_ AddItemTemplatesGuid` в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Дополнительные сведения о фильтрации и добавление элементов в **Добавление нового элемента** диалоговое окно, в разделе [элементов диалоговые окна добавления нового элемента, добавление](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)