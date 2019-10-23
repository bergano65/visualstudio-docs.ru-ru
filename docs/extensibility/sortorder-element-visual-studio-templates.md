---
title: Элемент SortOrder (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719914"
---
# <a name="sortorder-element-visual-studio-templates"></a>Элемент SortOrder (шаблоны Visual Studio)
Задает значение, используемое для упорядочения шаблона (помимо других шаблонов в той же категории), которое отображается в диалоговом окне **Создание проекта** или **Добавление нового элемента** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>Синтаксис

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 @No__t_0, представляющий значение порядка сортировки.

## <a name="remarks"></a>Заметки
 `SortOrder` — это необязательный элемент. Значение по умолчанию — 100, а все значения должны быть кратными 10.

 Элемент `SortOrder` игнорируется для шаблонов, созданных пользователем. Все созданные пользователем шаблоны сортируются в алфавитном порядке.

 Шаблоны с низким порядком сортировки отображаются в диалоговом окне **Создание проекта** или **Добавление элемента** перед шаблонами, имеющими значения с высоким порядком сортировки.

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для стандартного шаблона класса [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

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

 В этом примере элемент `SortOrder` относительно высокий. Вполне вероятно, что другие шаблоны [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] элементов будут иметь `SortOrder` значение ниже `290` и будут отображаться перед этим шаблоном в диалоговом окне **новый элемент** .

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)