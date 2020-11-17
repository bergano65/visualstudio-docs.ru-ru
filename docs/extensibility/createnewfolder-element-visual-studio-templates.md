---
title: Элемент Креатеневфолдер (шаблоны Visual Studio) | Документация Майкрософт
description: Сведения об элементе Креатеневфолдер и о том, как он определяет, не существует ли целевой каталог, в котором будет создан проект.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15633c2f701c813ca24c5484fd4108a86c57b05b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671583"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>Элемент Креатеневфолдер (шаблоны Visual Studio)
Определяет, следует проверять, существует ли целевой каталог, в котором создается проект. Если каталог существует, для проекта можно создать новый каталог. Этот параметр обычно переопределяется флагом реестра `NewProjectRequiresNewFolder(VsTemplate)` (`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`), который используют все распространенные типы проектов, чтобы определить, нужно ли создать проект в новом каталоге.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>Синтаксис

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Тип
 `Boolean`

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 В качестве текста следует использовать `true` или `false`, указав, будет ли создана новая папка при создании проекта на основе шаблона.

## <a name="remarks"></a>Комментарии
 Параметр `CreateNewFolder` является необязательным элементом. Значение по умолчанию — `true`.

 Значение, указанное в элементе `CreateNewFolder`, учитывается [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], только если базовая система поддерживает его.

## <a name="example"></a>Пример
 В следующем примере кода указано, что новая папка не создается при создании проекта на основе шаблона.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
