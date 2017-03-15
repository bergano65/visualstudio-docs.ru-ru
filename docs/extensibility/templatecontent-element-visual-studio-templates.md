---
title: "Элемент TemplateContent (шаблоны проектов Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent"
helpviewer_keywords: 
  - "TemplateContent - элемент [шаблоны проектов Visual Studio]"
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Элемент TemplateContent (шаблоны проектов Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает содержимое шаблона.  
  
## Синтаксис  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Указывает, выполнять ли построение решения при создании проекта из шаблона.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает организацию и содержимое имя многопроектных шаблонов.|  
|[Проект](../extensibility/project-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает файлы или каталоги, которые будут добавлены в проект.|  
|[Ссылки](../extensibility/references-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Задает ссылки на сборки, требуемые шаблоном элемента.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Необязательный элемент.<br /><br /> Указывает файл, который содержится в шаблоне.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Необязательный элемент.<br /><br /> Указывает все пользовательские параметры, которые должны использоваться при создании проекта или элемента на основе шаблона.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Содержит все метаданные для шаблона проекта, шаблона элемента или начального набора.|  
  
## Заметки  
 `TemplateContent` является обязательным элементом.  
  
## Пример  
 В следующем примере демонстрируются метаданные для шаблона проекта приложения [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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