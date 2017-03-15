---
title: "Элемент Description (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Description - элемент [шаблоны проектов Visual Studio]"
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Элемент Description (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает описание шаблона в том виде, в котором оно будет отображаться в диалоговом окне **Создать проект** или **Добавить новый элемент**.  
  
## Синтаксис  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Package`|Необязательный атрибут, предназначенный для сложных пользовательских скриптов.<br /><br /> GUID, который определяет идентификатор пакета Visual Studio.|  
|`ID`|Необязательный атрибут, предназначенный для сложных пользовательских скриптов.<br /><br /> Определяет идентификатор ресурса Visual Studio.|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон проекта к какой\-либо категории и определяет характеристики его отображения для диалоговых окон **Создать проект** или **Добавить новый элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным, если не используются атрибуты `Package` и `ID`.  
  
 Текст предоставляет описание шаблона.  
  
## Заметки  
 `Description` является обязательным дочерним элементом элемента `TemplateData`.  
  
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