---
title: Элемент RequiredFrameworkVersion (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40eefc62eef318bcd9c52a1cbbb966377b3616f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805814"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Элемент RequiredFrameworkVersion (шаблоны Visual Studio)

Указывает минимальную версию .NET Framework, требуемый шаблоном. Это вызывает **версию целевой платформы** раскрывающийся список для отображения в **новый проект** диалоговое окно. `RequiredFrameworkVersion` Элемент также определяет наименьшее значение в раскрывающемся списке.

> [!IMPORTANT]
> Начиная с Visual Studio 2017 версии 15.6, **версию целевой платформы** раскрывающийся список больше не является фильтром для отображаемых шаблонов в **шаблоны** раздел **новый проект** диалоговое окно. Вместо этого раскрывающегося списка функционирует как окно выбора платформы, для выбранного шаблона.

 \<VSTemplate> \<TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>Синтаксис

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как он отображается в любом категорию шаблона и **новый проект** или **Добавление нового элемента** диалоговое окно.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст должен быть минимальный номер версии платформы .NET Framework, которая необходима для шаблона.

## <a name="remarks"></a>Примечания

`RequiredFrameworkVersion` — это необязательный элемент. Этот элемент используется только в том случае, если шаблон поддерживает определенную минимальную версию (и более поздних версий, если таковые имеются) платформы .NET Framework. Если указать `RequiredFrameworkVersion` элемента и шаблона не поддерживает минимальный определенную версию .NET Framework, **версию целевой платформы** отображает раскрывающийся список, когда он неприменим.

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

В этом примере, минимальная версия .NET Framework, требуемый шаблоном, представленный `RequiredFrameworkVersion`, — 3.0. Проект, созданный с помощью этого шаблона можно целевой версии .NET Framework, начиная с версии 3.0.

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Использовать конкретную версию платформы .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
