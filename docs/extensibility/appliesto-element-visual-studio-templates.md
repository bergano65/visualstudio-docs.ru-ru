---
title: Элемент AppliesTo (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33288876d1a9101d96d4d2c0c0c7beb5e6f1ac72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352245"
---
# <a name="appliesto-element-visual-studio-templates"></a>Элемент AppliesTo (шаблоны Visual Studio)

Указывает необязательное выражение, которое соответствует один или несколько возможностей (см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Возможности предоставляются типами проектов через иерархию в виде свойства [__VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Таким образом шаблон может использоваться в нескольких типах проектов, имеющих общие применимые возможности.

Этот элемент является необязательным. В файле шаблона может быть не более одного экземпляра этого элемента. Этот элемент позволяет шаблону элемента быть применимым на основании возможностей выбранного в данный момент активного проекта. Его нельзя использовать, чтобы создать шаблон элемента неприменимым. Если `AppliesTo` отсутствует или выражение не проходит проверку применимости, `TemplateID` или `TemplateGroupID` используются, чтобы сделать шаблон применимым, как в предыдущих версиях продукта.

Представлено в обновлении 2 для Visual Studio 2013. Чтобы сослаться на правильную версию, см. в разделе [ссылки на сборки, представленные в Visual Studio 2013 SDK с обновлением 2](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Синтаксис

```xml
<AppliesTo>Capability1</AppliesTo>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Относит шаблон к определенной категории.|

## <a name="text-value"></a>Текстовое значение

Текстовое значение является обязательным. Этот текст задает возможности проекта.

Синтаксис допустимого выражения определяется следующим образом:

- Выражение возможности, такие как "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)».

- "&#124;" — Оператор OR.

- «&» И «+» символы являются операторами.

- "!" — оператор NOT.

- Скобки определяют порядок вычисления выражения.

- Значение NULL или пустое выражение считается совпадением.

- Возможности проекта могут содержать любой символ, кроме следующих зарезервированных символов: "'' :;,+-*/\\! ~&#124;& %$@^() ={}<> []? \t\b\n\r

## <a name="example"></a>Пример

В следующем примере показано три разных шаблона. `Template1` применяется ко всем типам проектов C# или к любому другому типу проектов, который поддерживает возможность `WindowsAppContainer`. `Template2` применяется ко всем проектам C# любого типа. `Template3` применяется к проектам C#, которые не являются проектами `WindowsAppContainer`.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)