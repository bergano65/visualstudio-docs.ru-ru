---
title: Элемент Максфрамеворкверсион (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702620"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Элемент Максфрамеворкверсион (шаблоны Visual Studio)

Указывает максимальную версию .NET Framework, необходимую для шаблона. Он определяет наибольшее значение, доступное в раскрывающемся списке **Версия целевой платформы** в диалоговом окне **Новый проект** . Чтобы пользователи могли выбрать версию платформы, необходимо также указать [рекуиредфрамеворкверсион](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) в качестве минимальной версии .NET Framework для шаблона.

> [!IMPORTANT]
> Начиная с Visual Studio 2017 версии 15,6, раскрывающийся список **версии целевой платформы** больше не является фильтром для отображаемых шаблонов в разделе " **шаблоны** " диалогового окна " **Создание проекта** ". Вместо этого раскрывающийся список **версии целевой платформы** выступает в качестве средства выбора платформы для выбранного шаблона.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Синтаксис

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Классификация шаблона и определение его отображения в диалоговом окне " **Новый проект** " или " **Добавление нового элемента** ".|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть самым высоким номером версии .NET Framework, разрешенным шаблоном.

## <a name="remarks"></a>Remarks

Параметр `MaxFrameworkVersion` является необязательным элементом. `MaxFrameworkVersion`Элемент следует опустить, если он не является обязательным, поэтому не следует случайно ограничить поддерживаемый диапазон версий .NET Framework для шаблона. Его также следует опустить, если .NET Framework неприменимо к шаблону.

## <a name="example"></a>Пример

В следующем примере показаны метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона класса.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

В этом примере максимальная версия .NET Framework, необходимая для шаблона, представленная `MaxFrameworkVersion` , — это 4.7.1. Проект, созданный с помощью этого шаблона, может ориентироваться .NET Framework версий до 4.7.1.

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
