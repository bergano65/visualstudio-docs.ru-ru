---
title: Элемент Folder (Шаблоны проекта Визуальной студии) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711465"
---
# <a name="folder-element-visual-studio-project-templates"></a>Элемент Folder (шаблоны проекта Visual Studio)
Упогоняет папку, которая будет добавлена в проект.

 \<VSTemplate \<> TemplateContent \< \<> проект> Folder>

## <a name="syntax"></a>Синтаксис

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Name`|Обязательный атрибут.<br /><br /> Название папки проекта.|
|`TargetFolderName`|Необязательный атрибут.<br /><br /> Укажите имя, чтобы дать папку при создании проекта из шаблона. Этот атрибут полезен для использования замены параметров для создания имени папки или именования папки с международной строкой, которая не может быть использована непосредственно в файле *.zip.*|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|`Folder`|Определяет папку для добавления в проект. `Folder`элементы могут `Folder` содержать элементы ребенка.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Определяет файл для добавления в проект.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Дополнительный элемент ребенка [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Примечания
 `Folder`является необязательным `Project`ребенком .

 Вы можете использовать любой из следующих методов для организации элементов проекта в папки в шаблоне:

- Включите папки в файл *шаблона .zip* и добавьте их в проект в *файле .vstemplate,* указав путь к файлу в `ProjectItem` элементах без `Folder` элементов. Рекомендуем использовать этот метод. Пример:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Включите папки в файл *шаблона .zip* и добавьте их `Folder` в проект в *файле .vstemplate* с элементами. Пример:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Не включайте папки в файл *шаблона .zip,* но добавляйте папки с `TargetFileName` помощью атрибута элемента. `ProjectItem` Пример:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Пример
 Следующий пример иллюстрирует метаданные для шаблона [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта для приложения Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент ProjectItem (шаблоны элементов Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
