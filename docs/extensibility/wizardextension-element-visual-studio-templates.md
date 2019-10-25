---
title: Элемент Визардекстенсион (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfd46573f70b31559f9d6c4749c142d763537764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748936"
---
# <a name="wizardextension-element-visual-studio-templates"></a>Элемент WizardExtension (шаблоны Visual Studio)
Содержит элементы регистрации для настройки мастера шаблонов.

 \<VSTemplate >... \<WizardExtension >

## <a name="syntax"></a>Синтаксис

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Обязательный элемент.<br /><br /> Указывает имя или строгое имя сборки, которая отображается в глобальном кэше сборок. Элемент `WizardExtension` должен содержать по крайней мере один элемент `Assembly`.|
|[фуллкласснаме](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Обязательный элемент.<br /><br /> Полное имя класса, реализующего интерфейс `IWizard`. Элемент `WizardExtension` должен содержать по крайней мере один элемент `FullClassName`.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Файле](../extensibility/vstemplate-element-visual-studio-templates.md)|Содержит все метаданные для шаблона проекта, шаблона элемента или начального набора.|

## <a name="remarks"></a>Заметки
 `WizardExtension` — необязательный дочерний элемент элемента `VSTemplate`.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для стандартного шаблона проекта для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения Windows.

```
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Практическое руководство. Использование мастеров для шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md)