---
title: MaxFrameworkVersion-элемент (шаблоны Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4bc28fcc35a4a59852ef6864886acff4dc87ef60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion - элемент (шаблоны Visual Studio)

Задает максимальную версию платформы .NET Framework, которые требуются для шаблона. Он определяет самое большое значение в **версию целевой платформы** раскрывающийся список **новый проект** диалогового окна. Чтобы пользователи могли выбрать версию платформы, необходимо также указать [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) как минимальная версия .NET Framework для шаблона.

> [!IMPORTANT]
> Начиная с Visual Studio 2017 г. версия 15,6, **версию целевой платформы** раскрывающийся список больше не является фильтром для шаблонов, отображаемых в **шаблоны** раздел **новый проект** диалогового окна. Вместо этого **версию целевой платформы** раскрывающийся список функционирует как окно выбора framework для выбранного шаблона.

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

## <a name="syntax"></a>Синтаксис

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон и определяет способ отображения либо **новый проект** или **Добавление нового элемента** диалоговое окно.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст должен быть наибольший номер версии платформы .NET Framework, может быть шаблоном.

## <a name="remarks"></a>Примечания

`MaxFrameworkVersion` — это необязательный элемент. `MaxFrameworkVersion` Элемент должен быть опущен, если он не является обязательным, так как не ограничивается случайно поддерживаемого диапазона .NET Framework версии шаблона. Его следует исключить, если .NET Framework не применяется к шаблону.

## <a name="example"></a>Пример

В следующем примере демонстрируется метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона класса.

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

В этом примере Максимальная версия платформы .NET Framework, которые требуются для шаблона в виде `MaxFrameworkVersion`, является 4.7.1. В проект, созданный с помощью этого шаблона можно целевой версии платформы .NET Framework до 4.7.1.

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
