---
title: Элемент AppliesTo (шаблоны Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e27ee1ab0ba42a82d61e2adbe9fb4c6c81cbb48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="appliesto-element-visual-studio-templates"></a>Элемент AppliesTo (шаблоны Visual Studio)
Задает необязательное выражение, которое будет соответствовать одной или нескольким возможностям. (см. <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Возможности предоставляются типами проектов через иерархию в виде свойства <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5>. Таким образом шаблон может использоваться в нескольких типах проектов, имеющих общие применимые возможности.  
  
 Этот элемент является необязательным. В файле шаблона может быть не более одного экземпляра этого элемента. Этот элемент позволяет шаблону элемента быть применимым на основании возможностей выбранного в данный момент активного проекта. Его нельзя использовать, чтобы создать шаблон элемента неприменимым. Если `AppliesTo` отсутствует или выражение не проходит проверку применимости, `TemplateID` или `TemplateGroupID` используются, чтобы сделать шаблон применимым, как в предыдущих версиях продукта.  
  
 Представлено в обновлении 2 для Visual Studio 2013. Для ссылки на правильную версию, см. [ссылки на сборки, представленные в Visual Studio 2013 SDK с обновлением 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<AppliesTo >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<AppliesTo>Capability1</AppliesTo>   
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Относит шаблон к определенной категории.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным. Этот текст задает возможности проекта.  
  
 Синтаксис допустимого выражения определяется следующим образом:  
  
-   Выражение возможности, такие как "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)».  
  
-   «&#124;» Является оператором OR.  
  
-   Символы "&" и "+" являются операторами AND.  
  
-   "!" — оператор NOT.  
  
-   Скобки определяют порядок вычисления выражения.  
  
-   Значение NULL или пустое выражение считается совпадением.  
  
-   Возможности проекта могут содержать любой символ, кроме следующих зарезервированных символов: «'' :;,+-*/\\! ~&#124;& %$@^()={} [] <>? \t\b\n\r  
  
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
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)