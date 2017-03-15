---
title: "Элемент ProvideDefaultName (шаблоны Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName - элемент [шаблоны проектов Visual Studio]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Элемент ProvideDefaultName (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Указывает, будет ли система работы с проектами [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создавать имя по умолчанию для шаблона в диалоговом окне **Добавить новый элемент** или **Создать проект**.  
  
## Синтаксис  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Текст должен иметь значение `true` или `false`, указывающее, требуется ли создавать имя по умолчанию для шаблона в диалоговом окне **Добавить новый элемент** или **Создать проект**.  
  
## Заметки  
 Элемент `ProvideDefaultName` является необязательным.  Значение по умолчанию — `true`.  
  
 Если элементу `ProvideDefaultName` задано значение `false`, то в полях **Имя** диалоговых окон **Добавить новый элемент** и **Создать проект** будет содержаться значение `<Введите_имя>`.  
  
 Используйте элемент [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md), чтобы указать имя по умолчанию для проекта или элемента в диалоговых окнах **Добавить новый элемент** и **Создать проект**.  
  
## Пример  
 В следующем примере кода элементу `ProvideDefaultName` задается значение `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)