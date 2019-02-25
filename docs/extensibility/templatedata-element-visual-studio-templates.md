---
title: Элемент TemplateData (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cd18443e36a48967b4eb9fdf24f8d5e7869c323
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700150"
---
# <a name="templatedata-element-visual-studio-templates"></a>Элемент TemplateData (шаблоны Visual Studio)
Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .

 \<VSTemplate > \<TemplateData >

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
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

| Элемент | Описание |
| - | - |
| [Name](../extensibility/name-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Указывает имя шаблона, как оно отображается в любом **новый проект** или **Добавление нового элемента** диалоговое окно. |
| [Описание](../extensibility/description-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Указывает описание шаблона, как оно отображается в любом **новый проект** или **Добавление нового элемента** диалоговое окно. |
| [Значок](../extensibility/icon-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Указывает путь и имя файла, файла образа, который служит в качестве значок, который отображается в либо **новый проект** или **Добавление нового элемента** диалоговом окне для шаблона. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Обязательный элемент.<br /><br /> Относит шаблон проекта, чтобы он отображался в указанной группе в **новый проект** диалоговое окно. |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Классифицирует шаблон проекта, таким образом, чтобы оно помещалось под указанной подкатегории в **новый проект** диалоговое окно. |
| [Идентификатор шаблона](../extensibility/templateid-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает идентификатор шаблона. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает идентификатор группы шаблона. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает значение, которое используется для размещения шаблона, других шаблонов в той же категории, как оно отображается в любом **новый проект** или **Добавление нового элемента** диалоговое окно. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, создан ли содержащей папки при создании экземпляра проекта. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Задает имя, система проектов Visual Studio создаст для проекта или элемента при его создании. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, будет ли в системе проектов Visual Studio создавать имя по умолчанию для проекта или элемента при его создании. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, могут ли быть созданы как временный проект. |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает ли **Обзор** кнопка доступна в **новый проект** диалоговом окне, чтобы пользователи могли легко изменять каталог по умолчанию, в котором сохранен проект. |
| [Скрытые](../extensibility/hidden-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, отображается ли в одном шаблоне **новый проект** или **Добавление нового элемента** диалоговое окно. |
| [Элемент NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает количество родительских категориях, которые будут отображаться в **новый проект** диалоговое окно. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Необязательный элемент. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Необязательный элемент.<br /><br /> Указывает ли **расположение** текстовое поле в **новый проект** диалоговое окно включено, отключено или скрытым для шаблона проекта. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Этот элемент используется в том случае, если шаблон поддерживает только определенную минимальную версию и более поздних версий, если таковое имеется, платформы .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, поддерживает ли шаблон главной страницы для веб-проектов. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает, поддерживает ли шаблон разделение кода, или модель страницы с выделенным кодом для веб-проектов. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Указывает ли шаблон является одинаковым для нескольких языков и ли **языка** параметр доступен из **новый проект** диалоговое окно. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Необязательный элемент.<br /><br /> Задает платформу, для которой предназначен шаблон проекта. Этот элемент указывает, что шаблон проекта используется для создания [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] приложения. |

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблон элемента или комплект для начала работы.|

## <a name="remarks"></a>Примечания
 `TemplateData` является обязательным элементом.

 Если необязательный элемент не указан, используется значение по умолчанию для этого элемента.

## <a name="example"></a>Пример
 В следующем примере показано метаданные для шаблона проекта [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] приложения.

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