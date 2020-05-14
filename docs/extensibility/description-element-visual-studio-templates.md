---
title: Элемент описания (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea10b43662d2818792dbc57aeac09a056cb63ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712256"
---
# <a name="description-element-visual-studio-templates"></a>Элемент описания (шаблоны Visual Studio)
Уотелит описание шаблона, как он появляется в **new Project** или **Добавить** new Item диалоговое окно.

 \<VSTemplate \<> TemplateData> \<Описание>

## <a name="syntax"></a>Синтаксис

```
<Description>
    Template Description
</Description>
```

```
<Description Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Package`|Дополнительный атрибут для расширенных пользовательских сценариев.<br /><br /> Идентификатор GUID, определяющий идентификатор пакета Visual Studio.|
|`ID`|Дополнительный атрибут для расширенных пользовательских сценариев.<br /><br /> Определяет идентификатор ресурса Visual Studio.|

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным, если не используются атрибуты `Package` и `ID`.

 В тексте приводится описание шаблона.

## <a name="remarks"></a>Примечания
 `Description`является необходимым элементом `TemplateData` ребенка элемента.

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
