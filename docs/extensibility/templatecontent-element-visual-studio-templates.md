---
title: Элемент TemplateContent (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2ad3f2a196a822bd6ec422fb6aeb50c9a043f7f
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562000"
---
# <a name="templatecontent-element-visual-studio-templates"></a>Элемент TemplateContent (шаблоны проектов Visual Studio)

Задает содержимое шаблона.

Иерархия элементов:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Синтаксис

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание:|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Указывает, следует ли для построения решения при создании проекта из шаблона.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание:|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает организацию и содержимое многопроектных шаблонов.|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает, файлов или каталогов, добавляемых в проект.|
|[Ссылки](../extensibility/references-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Задает ссылки на сборки, необходимые для шаблона элемента.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Необязательный элемент.<br /><br /> Указывает файл, который содержится в шаблоне.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает любые настраиваемые параметры, которые будут использоваться при создании проекта или элемента из шаблона.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблон элемента или комплект для начала работы.|

## <a name="remarks"></a>Примечания
 `TemplateContent` является обязательным элементом.

## <a name="example"></a>Пример
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.

```xml
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

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)