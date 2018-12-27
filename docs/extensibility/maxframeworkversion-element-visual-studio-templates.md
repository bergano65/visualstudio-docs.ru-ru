---
title: Элемент MaxFrameworkVersion (шаблоны Visual Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64f1550db7d2b3613bfa2e9d2da016cc1c6a3e4f
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561792"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Элемент MaxFrameworkVersion (шаблоны Visual Studio)

Указывает максимальную версию .NET Framework, требуемый шаблоном. Он определяет максимальное значение в **версию целевой платформы** раскрывающийся список **новый проект** диалоговое окно. Чтобы пользователи могли выбрать версию платформы, необходимо также указать [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) как минимальная версия .NET Framework для шаблона.

> [!IMPORTANT]
> Начиная с Visual Studio 2017 версии 15.6, **версию целевой платформы** раскрывающийся список больше не является фильтром для отображаемых шаблонов в **шаблоны** раздел **новый проект** диалоговое окно. Вместо этого **версию целевой платформы** раскрывающийся список функционирует как окно выбора платформы, для выбранного шаблона.

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

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

|Элемент|Описание:|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как он отображается в любом категорию шаблона и **новый проект** или **Добавление нового элемента** диалоговое окно.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст должен быть наибольший номер версии платформы .NET Framework, для которых разрешено с помощью шаблона.

## <a name="remarks"></a>Примечания

`MaxFrameworkVersion` — это необязательный элемент. `MaxFrameworkVersion` Элемент должен быть опущен, если только это не требуется, так как не для ограничения случайно поддерживаемый диапазон .NET Framework версий для шаблона. Он также если должна быть пропущена .NET Framework не применим к шаблону.

## <a name="example"></a>Пример

В следующем примере показано метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона класса.

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

В этом примере Максимальная версия .NET Framework, требуемый шаблоном, представленный `MaxFrameworkVersion`, является 4.7.1. Проект, созданный с помощью этого шаблона можно предназначенных для версий .NET Framework до 4.7.1.

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
