---
title: Добавление или изменение тегов в шаблонах проектов
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 4a5113fa7f420d58892e2737ec9196422486490e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038630"
---
# <a name="add-tags-to-project-templates"></a>Добавление тегов к шаблонам проектов

Начиная с версии 16.1 предварительной версии 2, в [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) можно добавлять теги языка, платформы и типа проекта к шаблонам проектов. Теги используются в двух местах в диалоговом окне нового проекта:

- Теги отображаются под описанием шаблона.

   ![Шаблон проекта с тегами в диалоговом окне нового проекта](media/npd-item-with-template-tags.png)

- По тегам можно выполнять поиск шаблонов и фильтрацию результатов поиска.

   ![Выполнение поиска и фильтрации в диалоговом окне нового проекта](media/npd-search-and-filter.png)

Вы можете добавить встроенные теги шаблонов Visual Studio или создать пользовательские теги, обновив XML-файл с расширением *.vstemplate*. Теги шаблонов доступны только в диалоговом окне нового проекта Visual Studio 2019. Они не влияют на отображение шаблона в предыдущих версиях Visual Studio.

## <a name="add-or-edit-tags"></a>Добавление или изменение тегов

Вы можете добавлять или изменять теги в XML-файле шаблона проекта с расширением *.vstemplate* в таких случаях:

* [при создании шаблона проекта](/visualstudio/ide/how-to-create-project-templates) с помощью мастера экспорта шаблонов;

* [при обновлении существующего шаблона проекта](/visualstudio/ide/how-to-update-existing-templates);

* [при создании шаблона проекта VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template).

## <a name="syntax"></a>Синтаксис

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Атрибуты

Следующие атрибуты являются необязательными и предназначены для сложных пользовательских сценариев.

|Атрибут|Описание|
|---------------|-----------------|
|`Package`|Идентификатор GUID, определяющий идентификатор пакета Visual Studio.|
|`ID`|Определяет идентификатор ресурса Visual Studio.|

Синтаксис:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Элементы

### <a name="child-elements"></a>Дочерние элементы

Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Обязательный.) Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавление нового элемента**.|

## <a name="text-value"></a>Текстовое значение

Текстовое значение является обязательным, если не используются атрибуты `Package` и `ID`.

Текстом передается имя шаблона.

## <a name="built-in-tags"></a>Встроенные теги

В Visual Studio доступен ряд встроенных тегов, при добавлении которых отображается локализованный ресурс. Ниже приведен перечень встроенных тегов с соответствующими значениями в скобках.

| Язык | Platform | Тип проекта |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Облако (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Консоль (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Классическое приложение (`desktop`) |
| Java (`java`) | Linux (`linux`) | Расширения (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Игры (`games`) |
| Python (`python`) | tvOS (`tvos`) | Интернет вещей (`iot`) |
| Язык запросов (`querylanguage`) | Windows (`windows`) | Библиотека (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Машинное обучение (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Мобильное приложение (`mobile`) |
| | | Office (`office`) |
| | | Другое (`other`) |
| | | Служба (`service`) |
| | | Тест (`test`) |
| | | UWP (`uwp`) |
| | | Интернет (`web`) |

## <a name="example"></a>Пример

В следующем примере показаны метаданные шаблона проекта для приложения Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
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

- [Справочник по схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Создание шаблонов проектов и элементов](/visualstudio/ide/creating-project-and-item-templates)
- [Настройка шаблонов проектов и элементов](/visualstudio/ide/customizing-project-and-item-templates)
- [Начало работы с шаблоном проекта VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)