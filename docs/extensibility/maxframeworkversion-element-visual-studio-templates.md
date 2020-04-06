---
title: Элемент MaxFrameworkVersion (Visual Studio Templates) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702620"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Элемент MaxFrameworkVersion (шаблоны Visual Studio)

Уотек максимальной версии рамочного соглашения .NET, требуемого шаблоном. Он определяет наивысшее значение, доступное в **целевой рамочной версии,** в диалоге **нового проекта.** Для того, чтобы пользователи могли выбрать рамочную версию, необходимо также указать [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) как минимальную версию .NET Framework для шаблона.

> [!IMPORTANT]
> Начиная с версии Visual Studio 2017 15.6, выпадение **целевой рамочной версии** больше не является фильтром для отображаемых шаблонов в разделе **шаблонов** диалога **New Project.** Вместо этого, **удаление целевой версии framework Version** функционирует как сборщик фреймворка для выбранного шаблона.

 \<VSTemplate \<> TemplateData> \<MaxFrameworkVersion>

## <a name="syntax"></a>Синтаксис

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Категоризирует шаблон и определяет, как он отображается либо в **новом проекте,** либо в диалоговом окне **Добавить новый элемент.**|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть самым высоким номером версии рамочного соглашения .NET, которое разрешено шаблоном.

## <a name="remarks"></a>Примечания

Параметр `MaxFrameworkVersion` является необязательным элементом. Элемент `MaxFrameworkVersion` должен быть опущен, если это не требуется, чтобы не случайно ограничить поддерживаемый диапазон версий .NET Framework для шаблона. Следует также не допускать, если в шаблоне не применяется рамочная система .NET.

## <a name="example"></a>Пример

Следующий пример иллюстрирует метаданные для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона стандартного класса.

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

В этом примере максимальная версия рамочного варианта .NET, `MaxFrameworkVersion`требуемая шаблоном, представленная, составляет 4.7.1. Проект, созданный с помощью этого шаблона, может быть ориентирован на версии .NET Framework до 4.7.1.

## <a name="see-also"></a>См. также

- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
