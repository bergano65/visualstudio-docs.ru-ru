---
title: Элемент RequiredFrameworkVersion (шаблоны Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc1a138c50c0fe13962f6601449eb3498d90398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137840"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Элемент RequiredFrameworkVersion (шаблоны Visual Studio)

Указывает минимальную версию платформы .NET Framework, которые требуются для шаблона. Это вызывает **версию целевой платформы** раскрывающийся список для отображения в **новый проект** диалогового окна. `RequiredFrameworkVersion` Элемент также определяет самое низкое значение в раскрывающемся списке.

> [!IMPORTANT]
> Начиная с Visual Studio 2017 г. версия 15,6, **версию целевой платформы** раскрывающийся список больше не является фильтром для шаблонов, отображаемых в **шаблоны** раздел **новый проект** диалогового окна. Вместо этого раскрывающегося списка функционирует как окно выбора framework для выбранного шаблона.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>Синтаксис

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Этот текст должен быть минимальный номер версии платформы .NET Framework, необходимой для шаблона.

## <a name="remarks"></a>Примечания

`RequiredFrameworkVersion` — это необязательный элемент. Этот элемент используется только в том случае, если шаблон поддерживает определенную минимальную версию (и более поздних версиях, если таковые имеются) платформы .NET Framework. При указании `RequiredFrameworkVersion` элемент и шаблон не поддерживает определенные Минимальная версия платформы .NET Framework, **версию целевой платформы** отображает раскрывающийся список, когда он неприменим.

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

В этом примере Минимальная версия платформы .NET Framework, которые требуются для шаблона в виде `RequiredFrameworkVersion`, 3.0. В проект, созданный с помощью этого шаблона можно целевой версии платформы .NET Framework, начиная с 3.0.

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Настройка конкретной версии платформы .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
