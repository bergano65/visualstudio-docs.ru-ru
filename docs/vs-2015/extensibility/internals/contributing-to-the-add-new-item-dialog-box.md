---
title: Влияющие на новый элемент диалоговое окно добавления | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb4db6bb361a47ca7c4d974950a99f4f1e9f395b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766561"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Добавление элементов в диалоговое окно "Добавить новый элемент"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтип проекта может предоставить полный каталог элементов для **Добавление нового элемента** диалоговое окно, зарегистрировав **Добавление элемента** шаблоны в разделе `Projects` подраздел реестра.  
  
## <a name="registering-add-new-item-templates"></a>Регистрация добавить новый элемент шаблоны  
 В этом разделе находится в папке **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** в реестре. Предположим, указанные ниже записи реестра [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проекта, упорядоченные по подтипом гипотетической проекта. Записи для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проекта, перечислены ниже.  
  
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
  
 `AddItemTemplates\TemplateDirs` Подраздел содержит записи реестра с путь к каталогу, где элементы становятся доступными в **Добавление нового элемента** помещаются диалоговое окно.  
  
 Среда автоматически загружает все `AddItemTemplates` данных в группе `Projects` подраздел реестра. Это могут быть данные для реализации базового проекта, а также данные для конкретных подтипов типов проектов. Каждый подтипа проекта определяется тип проекта `GUID`. Подтип проекта можно указать, что дополнительный набор `Add Item` шаблоны должны использоваться для экземпляра определенного предпочтительный проект, поддерживая `VSHPROPID_ AddItemTemplatesGuid` перечисления из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> реализацию, чтобы вернуть идентификатор GUID значение подтипа проекта. Если `VSHPROPID_AddItemTemplatesGuid` свойство не указано, используется GUID базового проекта.  
  
 Можно отфильтровать элементы в **Добавление нового элемента** диалоговое окно, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> интерфейс объекта средство инвентаризации программного обеспечения подтип проекта. Например, подтипом проекта, который реализует проект базы данных путем объединения [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проекта, можно отфильтровать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] элементы из **Добавление нового элемента** диалоговое окно путем реализации фильтрации и включить, можно добавить базы данных определенные элементы проекта, поддерживая `VSHPROPID_ AddItemTemplatesGuid` в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Дополнительные сведения о фильтрации и добавления элементов к **Добавление нового элемента** диалоговом окне см. в разделе [Добавление элементов, чтобы добавить новый элемент диалоговым окнам](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

