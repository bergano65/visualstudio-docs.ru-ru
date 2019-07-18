---
title: Элемент MaxFrameworkVersion (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194326"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion - элемент (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Указывает максимальную версию .NET Framework, требуемый шаблоном. Определяет, отображается ли в шаблоне **шаблоны** раздел **Добавление нового проекта** диалоговое окно, в зависимости от значения, выбранного в **версию целевой платформы** поле **Добавление нового проекта** диалоговое окно.  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет, как он отображается в любом категорию шаблона и **новый проект** или **Добавление нового элемента** диалоговое окно.|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является обязательным.  
  
 Этот текст должен быть наибольший номер версии платформы .NET Framework, для которых разрешено с помощью шаблона.  
  
## <a name="remarks"></a>Примечания  
 `MaxFrameworkVersion` — это необязательный элемент. Элемент в `TemplateData` раздел в файле VSTEMPLATE выступает в качестве фильтра для **шаблоны** раздел **Добавление нового проекта** диалоговое окно. Только шаблоны, чьи требования .NET Framework меньше, чем `MaxFrameworkVersion` значения элементов отображается, на основе значения, выбранного в **версию целевой платформы** поле **Добавление нового проекта**диалоговое окно. `MaxFrameworkVersion` Элемент должен быть опущен, если только это не требуется, так как не вызвать случайно шаблоны отображения при использовании более новой версии платформы .NET Framework.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метаданные для стандартного [!INCLUDE[csprcs](../includes/csprcs-md.md)] шаблона класса.  
  
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
  
 В этом примере Максимальная версия .NET Framework, требуемый шаблоном, представленный `MaxFrameworkVersion`, 3.5. Указанный выше шаблон будет отображаться только в том случае, при выборе 3.0 или 3.5 в **версию целевой платформы** поле **Добавление нового проекта** диалоговое окно.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
