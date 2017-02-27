---
title: "Элемент SupportsMasterPage (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage"
helpviewer_keywords: 
  - "<SupportsMasterPage> - элемент [шаблоны Visual Studio]"
  - "SupportsMasterPage - элемент [шаблоны Visual Studio]"
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Элемент SupportsMasterPage (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает, включен ли флажок **Выбрать главную страницу** в диалоговом окне **Добавить новый элемент**.  
  
## Синтаксис  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Указывает данные, относящие шаблон к какой\-либо категории и определяет характеристики его отображения для диалоговых окон **Создать проект** или **Создать элемент**.|  
  
## Текстовое значение  
 Текстовое значение является обязательным.  
  
 Текст должен иметь значение `true` или `false`, указывающее, доступен ли флажок **Выбрать главную страницу** в диалоговом окне **Добавить новый элемент**.  
  
## Заметки  
 Элемент `SupportsMasterPage` является необязательным.  Значение по умолчанию — `false`.  
  
 Элемент `SupportsMasterPage` доступен только для шаблонов веб\-элементов.  
  
## Пример  
 В следующем примере демонстрируются метаданные для веб\-проекта, включающего поддержку главной страницы.  
  
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
        <SupportsMasterPage>true</SupportsMasterPage>  
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