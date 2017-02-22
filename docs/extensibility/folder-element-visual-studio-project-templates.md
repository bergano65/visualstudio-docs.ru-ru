---
title: "Элемент Folder (шаблоны проектов Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder - элемент [шаблоны проектов Visual Studio]"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент Folder (шаблоны проектов Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает папку, которая будет добавлена в проект.  
  
## Синтаксис  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Name`|Обязательный атрибут.<br /><br /> Имя папки проекта.|  
|`TargetFolderName`|Необязательный атрибут.<br /><br /> Указывает имя, задаваемое папке при создании проекта из шаблона.  Этот атрибут полезен при использовании замены параметров для задания в качестве имени папки многоязыковой строки, которая не может использоваться непосредственно в ZIP\-файле, или для создания папки с таким именем.|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|`Folder`|Указывает папку, которая будет добавлена в проект.  Элементы `Folder` могут содержать дочерние элементы `Folder`.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Указывает файл, который будет добавлен в проект.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Проект](../extensibility/project-element-visual-studio-templates.md)|Необязательный дочерний элемент [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## Заметки  
 `Folder` является необязательным дочерним элементом `Project`.  
  
 Для организации элементов проекта в папках в шаблоне можно использовать любой из перечисленных ниже методов.  
  
-   Включить папки в ZIP\-файл шаблона и добавить их в проект в VSTEMPLATE\-файле, указав путь к файлу в элементах `ProjectItem` без элементов `Folder`.  Это рекомендуемый метод.  Например:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Включить папки в ZIP\-файл шаблона и добавить их в проект в VSTEMPLATE\-файле с помощью элементов `Folder`.  Например:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Не включать папки в ZIP\-файл шаблона, а добавить их с помощью атрибута `TargetFileName` элемента `ProjectItem`.  Например:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## Пример  
 В следующем примере демонстрируются метаданные для шаблона проекта Windows\-приложения [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Элемент ProjectItem \(шаблоны элементов Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)