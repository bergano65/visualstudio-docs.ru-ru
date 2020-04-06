---
title: ПрименяетсяК Элемент (Visual Studio Templates) Документы Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740075"
---
# <a name="appliesto-element-visual-studio-templates"></a>ПрименяетсяДля элемента (шаблоны Visual Studio)

Упомяните дополнительное выражение, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>соответствовать одному или более возможностям (см.). Возможности разоблачаются типами проектов через иерархию как [__VSHPROPID5 свойств. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Таким образом шаблон может использоваться в нескольких типах проектов, имеющих общие применимые возможности.

Этот элемент является необязательным. В файле шаблона может быть не более одного экземпляра этого элемента. Этот элемент позволяет шаблону элемента быть применимым на основании возможностей выбранного в данный момент активного проекта. Его нельзя использовать, чтобы создать шаблон элемента неприменимым. Если `AppliesTo` отсутствует или выражение не проходит проверку применимости, `TemplateID` или `TemplateGroupID` используются, чтобы сделать шаблон применимым, как в предыдущих версиях продукта.

Представлено в обновлении 2 для Visual Studio 2013. Для ссылки на правильную версию, см [Ссылки сборки доставлены в Visual Studio 2013 SDK Обновление 2](/previous-versions/dn632168(v=vs.120)).

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

Нет.

### <a name="child-elements"></a>Дочерние элементы

Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Относит шаблон к определенной категории.|

## <a name="text-value"></a>Текстовое значение

Текстовое значение является обязательным. Этот текст задает возможности проекта.

Синтаксис допустимого выражения определяется следующим образом:

- Выражение возможностей, например , "(VisualC &#124; CSharp) (MSTest &#124; NUnit)".

- Оператором "&#124;" является OR.

- Символы "&" и "Я" являются и операторами.

- "!" — оператор NOT.

- Скобки определяют порядок вычисления выражения.

- Значение NULL или пустое выражение считается совпадением.

- Возможности проекта могут быть любыми символами, за исключением этих\\зарезервированных символов: «''';,--»,&#124;&% <> .{} \t\b\n\r

## <a name="example"></a>Пример

В следующем примере показано три разных шаблона. `Template1`применяется либо ко всем типам проектов C, `WindowsAppContainer` либо к любому другому типу проекта, который поддерживает возможность. `Template2`применяется ко всем проектам C- `Template3` применяется к проектам C#, которые не являются проектами `WindowsAppContainer`.

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

- [Ссылка на схему шаблона Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
