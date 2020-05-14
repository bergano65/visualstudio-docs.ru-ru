---
title: Элемент SupportsMasterPage (шаблоны визуальной студии) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 384672303d00b72431820b98fa02d09e440a1de5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699451"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>Элемент SupportsMasterPage (шаблоны Visual Studio)
Уточняется, включен ли флажок **Select Master Page** в диалоговом поле Add New **Item.**

 \<>> \<> \<>

## <a name="syntax"></a>Синтаксис

```
<SupportsMasterPage> true/false </SupportsMasterPage>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Определяет данные, которые классифицируют шаблон, и определяет, как он отображается в поле диалога **New Project** или **New Item.**|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть `true` `false`либо или , указывая, является ли или нет **Выберите Мастер Страницы** флажок включен в поле диалога **Добавить новый элемент.**

## <a name="remarks"></a>Примечания
 Параметр `SupportsMasterPage` является необязательным элементом. Значение по умолчанию — `false`.

 Элемент `SupportsMasterPage` доступен только для шаблонов web-элементов.

## <a name="example"></a>Пример
 Ниже приводится пример, иллюстрирующий метаданные для веб-проекта, который включает поддержку главной страницы.

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
        <SupportsMasterPage>true</SupportsMasterPage>
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
