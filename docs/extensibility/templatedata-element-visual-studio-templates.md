---
title: Элемент templateData (Визуальные шаблоны студии) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699195"
---
# <a name="templatedata-element-visual-studio-templates"></a>Элемент TemplateData (шаблоны Visual Studio)
Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .

 \<>> \<templateData VSTemplate

## <a name="syntax"></a>Синтаксис

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы

| Элемент | Описание |
| - | - |
| [имя](../extensibility/name-element-visual-studio-templates.md); | Обязательный элемент.<br /><br /> Упоняет название шаблона, как он появляется в **new Project** или в диалоговом окне **Добавить новый элемент.** |
| [Описание](../extensibility/description-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Уотеляет описание шаблона, как он появляется в **new Project** или в диалоговом окне **Добавить новый элемент.** |
| [Значок](../extensibility/icon-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Для шаблона указывается путь и имя файла изображения, который служит в качестве значка, который отображается в поле для диалога **«Новый элемент»** или в диалоговом поле **«Добавить новый элемент».** |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Категоризирует шаблон проекта таким образом, чтобы он отосвобождался в указанной группе в диалоговом окне **нового проекта.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Классифицирует шаблон проекта таким образом, чтобы он отосвобождался под указанной подкатегорией в диалоговом окне **нового проекта.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Упоняет идентификатор шаблона. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Упоняет идентификатор группы шаблонов. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Определяет значение, которое используется для аранжировки шаблона, среди других шаблонов в той же категории, как это появляется в **new Project** или **Добавить new Item** диалоговое окно. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Определяет, создается ли содержащая папка на моментиализации проекта. |
| [По умолчаниюИмя](../extensibility/defaultname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Упоняет имя, которое система проекта Visual Studio будет генерировать для проекта или элемента при его создании. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, будет ли система проекта Visual Studio генерировать имя по умолчанию для проекта или элемента при его создании. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, можно ли создать проект как временный проект (только Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, доступна ли кнопка **«Просмотр»** в диалоговом окне **нового проекта,** чтобы пользователи могли легко изменять каталог по умолчанию, в котором сохраняется новый проект. |
| [Скрытые](../extensibility/hidden-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, отображается ли шаблон в поле для диалога **New Project** или **добавлении нового элемента.** |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уотеляет количество категорий родителей, которые будут отображать шаблон в диалоговом окне **нового проекта.** |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Необязательный элемент. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Необязательный элемент.<br /><br /> Уточняется, включено ли, отключено или скрыто для шаблона проекта текстовое поле **«Местоположение»** в диалоговом поле **Нового проекта.** |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Используйте этот элемент, если шаблон поддерживает только определенную минимальную версию, а более поздние версии, если таковые имеется, из системы .NET. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, поддерживает ли шаблон главную страницу для веб-проектов. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, поддерживает ли шаблон разделение кода, или модель страницы, лежащую за кодом, для веб-проектов. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Уточняется, является ли шаблон идентичным для нескольких языков и доступен ли параметр **Language** из диалогового окна **Нового Проекта.** |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Задает платформу, для которой предназначен шаблон проекта. Этот элемент указывает, что шаблон проекта используется [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] для создания приложений. |

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблона элементов или стартового комплекта.|

## <a name="remarks"></a>Примечания
 `TemplateData`является необходимым элементом.

 Если не включен дополнительный элемент, используется значение значения по умолчанию для этого элемента.

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
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
