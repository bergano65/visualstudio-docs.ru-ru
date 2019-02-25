---
title: Элемент SupportsLanguageDropDown (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8f94036a20d6c1b6963b39aa3d2b13e17a6e256
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678077"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Элемент SupportsLanguageDropDown (шаблоны Visual Studio)
Указывает, является ли шаблон веб-элемента идентичным для нескольких языков и ли **языка** включен параметр **Добавление нового элемента** диалоговое окно.

 \<VSTemplate > \<TemplateData > \<SupportsLanguageDropDown >

## <a name="syntax"></a>Синтаксис

```
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Этот текст должен быть либо `true` или `false`, указывающее, ли **языка** параметр доступен из **Добавление нового элемента** диалоговое окно.

## <a name="remarks"></a>Примечания
 `SupportsLanguageDropDown` — это необязательный элемент. Значение по умолчанию — `false`.

 `SupportsLanguageDropDown` Элемент доступен только для веб-шаблонов элементов.

 Если присвоено значение для этого элемента `true`, а затем шаблон элемента является одинаковым для всех языков программирования и **языка** будет включен параметр **Добавление нового элемента** диалоговое окно. Этот параметр позволяет выбрать язык программирования для нового элемента, который вы хотите создать из шаблона.

## <a name="example"></a>Пример
 В следующем примере задается для отображения **языка** раскрывающийся список параметра.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)