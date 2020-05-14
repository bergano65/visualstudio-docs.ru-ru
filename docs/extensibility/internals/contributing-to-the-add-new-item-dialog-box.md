---
title: Вклад в добавить новый пункт Диалог Box (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709278"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Внесите свой вклад в диалоговую коробку Добавить новый элемент
Подтип проекта может предоставить полный новый каталог элементов для диалогового окна **Add New Item,** зарегистрировав шаблоны **Add Item** в подключке реестра **проектов.**

## <a name="register-add-new-item-templates"></a>Зарегистрируйтесь Добавить новые шаблоны элемента
 Этот раздел расположен в соответствии с **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0 "Проекты** в реестре. Записи реестра ниже [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предполагают проект, агрегированный гипотетическим подтипом проекта. Записи для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекта перечислены ниже.

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

 Подключка **AddItemTemplates-TemplateDirs** содержит записи реестра с пути к каталогу, где размещаются элементы, доступные в диалоговом поле **Add New Item.**

 Среда автоматически загружает все данные **AddItemTemplates** в подключку реестра **проектов.** Эти данные могут включать данные для реализации базовых проектов, а также данные по конкретным типам подтипов проекта. Каждый подтип проекта идентифицируется по типу **проекта GUID.** Подтип проекта может указать, что альтернативный набор шаблонов **Add Item** должен использоваться `VSHPROPID_ AddItemTemplatesGuid` для конкретного <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ароматизированного экземпляра проекта, поддерживая перечисление из реализации для возврата значения GUID подтипа проекта. Если `VSHPROPID_AddItemTemplatesGuid` свойство не указано, используется базовый проект GUID.

 Можно фильтровать элементы в диалоговом окне <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> **Добавления нового элемента,** реализовав интерфейс на объекте агрегатора подтипа проекта. Например, подтип проекта, реализующий проект базы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] данных путем [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] агрегирования проекта, может фильтровать определенные элементы из окна диалога **Add New** Item `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>путем реализации фильтрации, а в свою очередь, добавлять элементы, связанные с проектом базы данных, поддерживая в. Для получения дополнительной информации о фильтрации и добавлении элементов в диалоговую коробку **Добавить новый элемент** см. [Add items to the Add New Item dialog box](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
