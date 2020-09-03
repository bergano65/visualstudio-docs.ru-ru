---
title: Вклад в диалоговое окно "Добавление нового элемента" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197024"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Добавление элементов в диалоговое окно "Добавить новый элемент"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтип проекта может предоставлять полный новый каталог элементов для диалогового окна **Добавление нового элемента** путем регистрации **добавления шаблонов элементов** в `Projects` подразделе реестра.  
  
## <a name="registering-add-new-item-templates"></a>Регистрация добавления новых шаблонов элементов  
 Этот раздел находится в разделе **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\projects** в реестре. Приведенные ниже записи реестра предполагают, что [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проект агрегирован по гипотетическому подтипу проекта. Ниже перечислены записи для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проекта.  
  
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
  
 `AddItemTemplates\TemplateDirs`Подраздел содержит записи реестра с путем к каталогу, в который помещаются элементы, доступные в диалоговом окне **Добавление нового элемента** .  
  
 Среда автоматически загружает все данные из `AddItemTemplates` `Projects` подраздела реестра. Сюда могут входить данные для базовых реализаций проекта, а также данные для конкретных типов подтипов проектов. Каждый подтип проекта определяется типом проекта `GUID` . Подтип проекта может указывать, что `Add Item` для конкретного экземпляра проекта с определенным типом следует использовать альтернативный набор шаблонов, поддерживая `VSHPROPID_ AddItemTemplatesGuid` Перечисление <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> в реализации, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> чтобы вернуть значение идентификатора GUID подтипа проекта. Если `VSHPROPID_AddItemTemplatesGuid` свойство не задано, используется базовый идентификатор проекта.  
  
 Можно отфильтровать элементы в диалоговом окне **Добавление нового элемента** , реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> интерфейс для объекта агрегатора подтипа проекта. Например, подтип проекта, который реализует проект базы данных путем статистической обработки [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проекта, может фильтровать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] определенные элементы в диалоговом окне **Добавление нового элемента** путем реализации фильтрации и, в свою очередь, может добавлять определенные элементы проекта базы данных путем поддержки `VSHPROPID_ AddItemTemplatesGuid` в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Дополнительные сведения о фильтрации и добавлении элементов в диалоговом окне " **Добавление нового элемента** " см. в разделе [Добавление элементов в диалоговые окна Добавление нового элемента](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
