---
title: Элемент WizardData (Визуальные шаблоны студии) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3f9d2e971d944b964f4b194d1324ff960fbd24
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740394"
---
# <a name="wizarddata-element-visual-studio-templates"></a>Элемент WizardData (шаблоны Visual Studio)

Определяет пользовательские XML

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Синтаксис

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы

В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

Нет.

### <a name="child-elements"></a>Дочерние элементы

Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблона элементов или стартового комплекта.|

## <a name="text-value"></a>Текстовое значение

Текстовое значение является необязательным.

В этом тексте указывается пользовательский XML для передачи в пользовательское расширение мастера, указанное в элементе [WizardExtension.](../extensibility/wizardextension-element-visual-studio-templates.md)

## <a name="remarks"></a>Примечания

Любой XML может быть указан в этом элементе. XML будет передан в качестве параметра пользовательскому расширению мастера, что позволит расширению использовать содержимое этого элемента. Проверка этих данных не проводится.

Содержимое элемента **WizardData** передается без изменений, как параметр внутри строки словаря параметров в методе. `IWizard.RunStarted` Словарный ключ называется `$wizarddata$`.

## <a name="example"></a>Пример

Следующий пример иллюстрирует метаданные для стандартного шаблона проекта для приложения Windows.

```xml
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
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Элемент WizardExtension (шаблоны Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Практическое руководство. Использование мастеров для шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md)
