---
title: Элемент проекта (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702006"
---
# <a name="project-element-visual-studio-templates"></a>Элемент проекта (шаблоны Visual Studio)
Определяет файлы или каталоги для добавления в проект.

 \<VSTemplate \<> TemplateContent> \<проект>

## <a name="syntax"></a>Синтаксис

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`File`|Обязательный атрибут.<br /><br /> Упоняет название файла проекта в файле шаблона *.zip.*|
|`ReplaceParameters`|Необязательный атрибут.<br /><br /> Значение Boolean, которое определяет, имеет ли файл проекта значения параметров, которые должны быть заменены при создании проекта из шаблона. Значение по умолчанию: `false`.|
|`TargetFileName`|Необязательный атрибут.<br /><br /> Упоняет название файла проекта при создании проекта из шаблона.|
|`IgnoreProjectParameter`|Необязательный атрибут.<br /><br /> Уточняется, следует ли добавлять проект к текущему решению. Если значение пользовательского параметра ,$*myCustomParameter*$" существует в файле замены параметров, проект создается, но не добавляется как часть открытого решения, наиболее открытого в настоящее время.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Папку](../extensibility/folder-element-visual-studio-project-templates.md)|Необязательный элемент.<br /><br /> Определяет папку для добавления в проект.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Необязательный элемент.<br /><br /> Определяет файл для добавления в проект.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Обязательный элемент.|

## <a name="remarks"></a>Примечания
 `Project` — необязательный дочерний элемент элемента `TemplateContent`.

 Элемент `Project` используется для оpecifiy проекта, и, следовательно, действителен только в шаблонах проекта.

 `Project`элементы могут иметь элементы [Folder](../extensibility/folder-element-visual-studio-project-templates.md) детей или элементы `Folder` `ProjectItem` [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) детей, но не смесь как и элементов детей.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]автоматически переименовывает имя файла проекта на основе имени, введенного пользователем в диалоговом окне **нового проекта.** Используйте `TargetFileName` атрибут, если требуется предоставить альтернативное имя файла для файлов проекта, созданных с помощью шаблона.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] для шаблона проекта для приложения.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент ProjectItem (шаблоны проекта Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Элемент Folder (шаблоны проекта Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
