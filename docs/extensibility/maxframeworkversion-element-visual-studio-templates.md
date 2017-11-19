---
title: "MaxFrameworkVersion-элемент (шаблоны Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da1b30274254c5c1dd81ad20dd64e8749672f96e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion - элемент (шаблоны Visual Studio)
Задает максимальную версию платформы .NET Framework, которые требуются для шаблона. Определяет, отображается ли в шаблоне **шаблоны** раздел **Добавление нового проекта** диалоговом на основе значения, выбранного в **версию целевой платформы** поле **Добавление нового проекта** диалоговое окно.  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон и определяет способ отображения либо **новый проект** или **Добавление нового элемента** диалоговое окно.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть наибольший номер версии платформы .NET Framework, может быть шаблоном.  
  
## <a name="remarks"></a>Примечания  
 `MaxFrameworkVersion` — это необязательный элемент. Элемент в `TemplateData` раздел VSTEMPLATE-файл выступает в качестве фильтра для **шаблоны** раздел **Добавление нового проекта** диалоговое окно. Только шаблоны, чьи требования .NET Framework меньше, чем `MaxFrameworkVersion` значения элементов отображается, в зависимости от значения, выбранного в **версию целевой платформы** поле **Добавление нового проекта**диалоговое окно. `MaxFrameworkVersion` Элемент должен быть опущен, если он не является обязательным, так как не заставить случайно шаблоны отображения при их использовании в новых версиях платформы .NET Framework.  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется метаданные для стандартного [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] шаблона класса.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 В этом примере Максимальная версия платформы .NET Framework, которые требуются для шаблона в виде `MaxFrameworkVersion`, — 3.5. Шаблон будет отображаться только при выборе 3.0 или 3.5 в **версию целевой платформы** поле **Добавление нового проекта** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)