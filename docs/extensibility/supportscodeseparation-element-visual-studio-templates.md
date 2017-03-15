---
title: "Элемент SupportsCodeSeparation (шаблоны проектов Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation"
helpviewer_keywords: 
  - "<SupportsCodeSeparation> - элемент [шаблоны Visual Studio]"
  - "SupportsCodeSeparation - элемент [шаблоны Visual Studio]"
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Элемент SupportsCodeSeparation (шаблоны проектов Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает, включен ли флажок **Размещать код в отдельном файле** в диалоговом окне **Добавить новый элемент**.  
  
## Синтаксис  
  
```  
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Относит шаблон проекта к какой\-либо категории и определяет характеристики его отображения для диалоговых окон **Создать проект** или **Создать элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Текст должен иметь значение `true` или `false`, указывающее, включен ли флажок **Размещать код в отдельном файле** в диалоговом окне **Добавить новый элемент**.  
  
## Заметки  
 Элемент `SupportsCodeSeparation` является необязательным.  Значение по умолчанию — `false`.  
  
 Элемент `SupportsCodeSeparation` доступен только для шаблонов веб\-элементов.  
  
 Разделение кода или модель страницы с выделенным кодом позволяет поместить разметку в один файл, а программный код — в другой.  Эта модель используется в [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и других языках .NET.  
  
## Пример  
 В следующем примере задается отображение параметра **Размещать код в отдельном файле**.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsCodeSeparation>true</SupportsCodeSeparation>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)