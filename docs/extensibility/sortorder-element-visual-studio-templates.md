---
title: Элемент SortOrder (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699958"
---
# <a name="sortorder-element-visual-studio-templates"></a>Элемент SortOrder (шаблоны Visual Studio)
Определяет значение, которое используется для аранжировки шаблона, среди других шаблонов в той же категории, как это появляется в **new Project** или **Добавить new Item** диалоговое окно.

 \<VSTemplate \<> TemplateData> \<> SortOrder

## <a name="syntax"></a>Синтаксис

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Значение `integer` заказа сортировки представляет собой значение сортировки.

## <a name="remarks"></a>Примечания
 Параметр `SortOrder` является необязательным элементом. Значение по умолчанию 100, и все значения должны быть кратными 10.

 Элемент `SortOrder` игнорируется для созданных пользователем шаблонов. Все созданные пользователем шаблоны сортируются в алфавитном порядке.

 Шаблоны с низкими значениями заказов сортировки отображаются либо в поле диалога **New Project** или New **Add Item** перед шаблонами с высокими значениями порядка сортировки.

## <a name="example"></a>Пример
 Следующий пример иллюстрирует метаданные для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона стандартного класса.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 В этом примере `SortOrder` элемент относительно высок. Вполне вероятно, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] что другие `SortOrder` шаблоны `290` элементов будут иметь значение ниже, чем и появится до этого шаблона в поле диалога **New Item.**

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
