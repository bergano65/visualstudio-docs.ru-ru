---
title: ОбязательныйЭлементКарнойверсии (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701501"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Элемент RequiredFrameworkVersion (шаблоны Visual Studio)

Уотек минимальной версии рамочного соглашения .NET, требуемого шаблоном. Это приводит к тому, что в диалоге **нового проекта** отображается версия **Целевой рамочной версии.** Элемент `RequiredFrameworkVersion` также определяет наименьшее значение, доступное в отсечке.

> [!IMPORTANT]
> Начиная с версии Visual Studio 2017 15.6, выпадение **целевой рамочной версии** больше не является фильтром для отображаемых шаблонов в разделе **шаблонов** диалога **New Project.** Вместо этого выпадение функций в качестве сборщика фреймворка для выбранного шаблона.

 \<VSTemplate \<> TemplateData> \<необходимая>

## <a name="syntax"></a>Синтаксис

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 Текст должен быть минимальным номером версии рамочного индекса .NET, который необходим для шаблона.

## <a name="remarks"></a>Примечания

Параметр `RequiredFrameworkVersion` является необязательным элементом. Используйте этот элемент только в том случае, если шаблон поддерживает определенную минимальную версию (а позже версии, если таковые имеется) рамочного соглашения .NET. Если вы `RequiredFrameworkVersion` указываете элемент и шаблон не поддерживает конкретную минимальную версию рамочного соглашения .NET, то **выпадение целевой рамочной версии** отображается, когда это неприменимо.

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

В этом примере минимальная версия рамочного индекса .NET, `RequiredFrameworkVersion`требуемая шаблоном, представленная , составляет 3,0. Проект, созданный с помощью этого шаблона, может таргетировать версии .NET Framework, начиная с 3.0.

## <a name="see-also"></a>См. также

- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Общие сведения о настройке целевой платформы](../ide/visual-studio-multi-targeting-overview.md)
