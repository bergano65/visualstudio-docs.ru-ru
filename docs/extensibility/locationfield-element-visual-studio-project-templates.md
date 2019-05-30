---
title: Элемент LocationField (шаблоны проектов Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b440595207cee6a146e6d85ee5e9f7c492ee3eee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309173"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Элемент LocationField (шаблоны проектов Visual Studio)
Указывает ли **расположение** текстовое поле в **новый проект** включен, отключен или скрытым для шаблона проекта диалоговое окно.

 \<VSTemplate> \<TemplateData> \<LocationField>

## <a name="syntax"></a>Синтаксис

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как отображается ли он в категорию шаблона и **новый проект**.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Ниже перечислены значения допустимый текст.

- `Enabled`, который указывает на то, что **расположение** поле **новый проект** становится доступным поле диалогового окна.

- `Disabled`, который указывает на то, что **расположение** поле **новый проект** диалоговое окно отключено.

- `Hidden`, который указывает на то, что **расположение** поле **новый проект** диалоговое окно является скрытым.

## <a name="remarks"></a>Примечания
 Значение по умолчанию — `Enabled`.

 **Расположение** текстовое поле в **новый проект** диалоговое окно позволяет пользователям изменить каталог по умолчанию, в котором сохраняются новые проекты.

 Значение, указанное в `Location` элемент только будет соблюдаться системой диалоговое окно, если базовая система поддерживает его.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для шаблона [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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