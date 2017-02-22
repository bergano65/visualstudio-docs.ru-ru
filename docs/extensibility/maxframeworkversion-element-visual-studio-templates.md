---
title: "MaxFrameworkVersion - элемент (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> - элемент (шаблоны Visual Studio)"
  - "MaxFrameworkVersion - элемент (шаблоны Visual Studio)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# MaxFrameworkVersion - элемент (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает максимальную версию платформы .NET Framework, которая требуется для этого шаблона.  Это определяет, отображается ли шаблон в разделе **Шаблоны** диалогового окна **Добавить новый проект** в зависимости от значения, выбранного в поле **Целевая версия Framework** диалогового окна **Добавить новый проект**.  
  
## Синтаксис  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
 Отсутствует.  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон к какой\-либо категории и определяет, как он отображается в диалоговом окне **Создать проект** или **Добавить новый элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 В тексте необходимо указать самую высокую из возможных в данном шаблоне версию платформы .NET Framework.  
  
## Заметки  
 Элемент `MaxFrameworkVersion` является необязательным.  Элемент в части `TemplateData` VSTEMPLATE\-файла действует как фильтр для раздела **Шаблоны** диалогового окна **Добавить новый проект**.  Будут отображаться только шаблоны с требованиями .NET Framework меньше, чем значения элемента `MaxFrameworkVersion`, в зависимости от значения, выбранного в поле **Целевая версия Framework** диалогового окна **Добавить новый проект**.  Элемент `MaxFrameworkVersion` должен быть опущен, если он не требуется, чтобы не вызвать случайно, что шаблоны отображаются при их использовании с более новыми версиями .NET Framework.  
  
## Пример  
 В следующем примере демонстрируются метаданные для стандартного шаблона элемента класса [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
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
  
 В этом примере максимальная требуемая для шаблона версия .NET Framework, представленная `MaxFrameworkVersion`, — 3.5.  Шаблон выше будет отображаться только при выборе 3.0 или 3.5 в поле **Целевая версия Framework** диалогового окна **Добавить новый проект**.  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)