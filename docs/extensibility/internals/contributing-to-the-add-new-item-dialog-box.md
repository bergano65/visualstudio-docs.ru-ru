---
title: Влияющие на новый элемент диалоговое окно добавления | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77008b6a4403270c77e24607fc0f4f6f4456296e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596624"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Участвовать в диалоговом окне Добавление нового элемента
Подтип проекта может предоставить полный каталог элементов для **Добавление нового элемента** диалоговое окно, зарегистрировав **Добавление элемента** шаблоны в разделе **проекты** подраздел реестра.

## <a name="register-add-new-item-templates"></a>Регистрация шаблонов элементов
 В этом разделе находится в папке **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** в реестре. Предположим, указанные ниже записи реестра [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, упорядоченные по подтипом гипотетической проекта. Записи для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, перечислены ниже.

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

 **AddItemTemplates\TemplateDirs** подраздел содержит записи реестра с путь к каталогу, где элементы становятся доступными в **Добавление нового элемента** помещаются диалоговое окно.

 Среда автоматически загружает все **AddItemTemplates** данных в группе **проекты** подраздел реестра. Эти данные могут содержать данные для реализации базового проекта, а также данные для конкретных подтипов типов проектов. Каждый подтипа проекта определяется тип проекта **GUID**. Подтип проекта можно указать, что дополнительный набор **Добавление элемента** шаблоны должны использоваться для экземпляра определенного предпочтительный проект, поддерживая `VSHPROPID_ AddItemTemplatesGuid` перечисления из <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Реализация для возврата значения GUID подтипа проекта. Если `VSHPROPID_AddItemTemplatesGuid` свойство не указано, используется GUID базового проекта.

 Можно отфильтровать элементы в **Добавление нового элемента** диалоговое окно, реализовав <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> интерфейс объекта средство инвентаризации программного обеспечения подтип проекта. Например, подтипом проекта, который реализует проект базы данных путем объединения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта, можно отфильтровать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] элементы из **Добавление нового элемента** диалоговое окно путем реализации фильтрации и включить, можно добавить элементов конкретных проектов баз данных, поддерживая `VSHPROPID_ AddItemTemplatesGuid` в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Дополнительные сведения о фильтрации и добавления элементов к **Добавление нового элемента** диалоговом окне см. в разделе [Добавление элементов в диалоговом окне Add New Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)