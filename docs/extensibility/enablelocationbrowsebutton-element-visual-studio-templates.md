---
title: EnableLocationBrowseButton Элемент (Visual Studio шаблоны) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711990"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Элемент EnableLocationBrowseButton (шаблоны Визуальной студии)
Уточняется, доступна ли кнопка **«Просмотр»** в диалоговом окне **нового проекта,** чтобы пользователи могли легко изменять каталог по умолчанию, в котором сохраняется новый проект.

 \<VSTemplate \<> TemplateData> \<EnableLocationButton>

## <a name="syntax"></a>Синтаксис

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть `true` `false`либо или , с указанием того, следует ли отображать кнопку **просмотра** на поле диалога **Нового проекта.**

## <a name="remarks"></a>Примечания
 Параметр `EnableLocationBrowseButton` является необязательным элементом. Значение по `true`умолчанию, которое отображает кнопку **Просмотра** в поле диалога **Нового проекта.**

 В диалоговом окне **нового проекта** текстовый окне **Местоположения** определяет каталог, где сохраняется новый проект. Кнопка **«Просмотр»** поможет изменить этот каталог, отобразив диалоговую коробку **«Местоположение проекта»,** которая позволяет легко перемещаться по другому каталогу, доступному с вашего компьютера, а затем выбрать его в качестве каталога, в котором сохраняется новый проект.

## <a name="example"></a>Пример
 Следующий пример иллюстрирует метаданные [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] для приложения Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
