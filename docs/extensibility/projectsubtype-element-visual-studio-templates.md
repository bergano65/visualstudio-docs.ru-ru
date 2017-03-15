---
title: "Элемент ProjectSubType (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> - элемент [шаблоны Visual Studio]"
  - "ProjectSubType - элемент [шаблоны Visual Studio]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Элемент ProjectSubType (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Классифицирует шаблон в подкатегорию значения, указанного в элементе `ProjectType`.  
  
## Синтаксис  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон проекта к какой\-либо категории и определяет характеристики его отображения для диалоговых окон **Создать проект** или **Добавить новый элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Это значение задает подкатегорию шаблона.  
  
## Заметки  
 `ProjectSubType` является необязательным дочерним элементом для `TemplateData`.  
  
 Элемент `ProjectSubType` предоставляет подкатегорию элементу [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md).  Значение может включать:  
  
-   `SmartDevice-NETCFv1`: указывает, что выбран шаблон, поддерживающий [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 1.0.  
  
-   `SmartDevice-NETCFv2`: указывает, что выбран шаблон, поддерживающий [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 2.0.  
  
 Если элемент содержит элемент `ProjectType` со значением `Web`, то `ProjectSubType` задает язык программирования шаблона.  Этот элемент может принимать следующие значения:  
  
-   `CSharp`: задает создание шаблоном веб\-проекта или элемента [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
-   `VisualBasic`: задает создание шаблоном веб\-проекта или элемента [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Пример  
 В следующем примере демонстрируются метаданные для шаблона проекта приложения для устройств [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], предназначенных для [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] версии 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Элемент ProjectType \(шаблоны Visual Studio\)](../extensibility/projecttype-element-visual-studio-templates.md)