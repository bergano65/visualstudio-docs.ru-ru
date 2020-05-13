---
title: Элемент LocationField (Шаблоны проекта визуальной студии) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702886"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Элемент LocationField (шаблоны проекта Visual Studio)
Определяет, включено ли, отключено или скрыто для шаблона проекта текстовое поле **«Местоположение»** в диалоговом поле **Нового проекта.**

 \<VSTemplate \<> TemplateData> \<LocationField>

## <a name="syntax"></a>Синтаксис

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Категоризирует шаблон и определяет, как он отображается в **новом проекте.**|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Действительные значения текста:

- `Enabled`, который указывает, что окно **местоположения** нового окна диалога **проекта** включено.

- `Disabled`, который указывает, что поле **расположение** нового окна диалога **проекта** отключено.

- `Hidden`, который указывает, что поле **расположение** нового диалога **проекта** скрыто.

## <a name="remarks"></a>Примечания
 Значение по умолчанию — `Enabled`.

 Текстовое окно **местоположения** в диалоговом поле **Нового проекта** позволяет пользователям изменять каталог по умолчанию, в котором сохраняются новые проекты.

 Значение, указанное `Location` в элементе, удостоилось диалогового окна только в том случае, если базовая проектная система поддерживает его.

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
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
