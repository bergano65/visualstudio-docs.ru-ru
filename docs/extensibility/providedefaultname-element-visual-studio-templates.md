---
title: ОбеспечитьDefaultName Элемент (Visual Studio шаблоны) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701720"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>Элемент ProvideDefaultName (шаблоны Visual Studio)
Уточняется, будет [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ли проектная система генерировать имя по умолчанию для шаблона в диалоговом окне **Добавления нового элемента** или **нового проекта.**

 \<VSTemplate \<> TemplateData> \<provideDefaultName>

## <a name="syntax"></a>Синтаксис

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 Текст должен быть `true` `false`либо, либо , с указанием того, следует ли создавать имя по умолчанию для шаблона в **добавлении нового элемента** или нового диалога **проекта.**

## <a name="remarks"></a>Примечания
 Параметр `ProvideDefaultName` является необязательным элементом. Значение по умолчанию — `true`.

 Если `ProvideDefaultName` `false`элемент, **имя** коробки **Добавить новый пункт** и **новый** `<Enter_name>`проект диалоговых коробок содержат значение.

 Используйте элемент [DefaultName,](../extensibility/defaultname-element-visual-studio-templates.md) чтобы указать имя проекта по умолчанию или элемент в диалоговых коробках **Добавить новый элемент** и **новый проект.** Когда значение `ProvideDefaultName` элемента, `true`упущение `DefaultName` элемента для проектов заполняет поле диалога с именем шаблона, то есть значение от элемента [имя.](../extensibility/name-element-visual-studio-templates.md)

## <a name="example"></a>Пример
 Следующий пример кода `ProvideDefaultName` устанавливает `false`элемент для .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
