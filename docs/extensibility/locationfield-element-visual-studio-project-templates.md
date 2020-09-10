---
title: Элемент LocationField (шаблоны проектов Visual Studio)
titleSuffix: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9aafe51669bcc95d6024b5a3fd749ba70ea8ddc7
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2020
ms.locfileid: "89739127"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Элемент Локатионфиелд (шаблоны проектов Visual Studio)
Указывает, будет ли текстовое поле **Расположение** в диалоговом окне **Новый проект** включено, отключено или скрыто для шаблона проекта.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Классификация шаблона и определение его отображения в **новом проекте**.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Допустимые текстовые значения:

- `Enabled`, который указывает, что в поле **Расположение** диалогового окна **Новый проект** включен.

- `Disabled`, который указывает, что поле **Расположение** диалогового окна **Новый проект** отключено.

- `Hidden`, который указывает, что поле **Расположение** диалогового окна **Новый проект** скрыто.

## <a name="remarks"></a>Примечания
 Значение по умолчанию — `Enabled`.

 Текстовое поле **Расположение** в диалоговом окне **Новый проект** позволяет пользователям изменять каталог по умолчанию, в котором сохраняются новые проекты.

 Значение, указанное в `Location` элементе, учитывается в диалоговом окне только в том случае, если базовая система проектов поддерживает его.

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
