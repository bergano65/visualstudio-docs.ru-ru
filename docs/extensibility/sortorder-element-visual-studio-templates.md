---
title: "Элемент SortOrder (шаблоны Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> - элемент [шаблоны Visual Studio]"
  - "SortOrder - элемент [шаблоны Visual Studio]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент SortOrder (шаблоны Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает значение, с помощью которого шаблон упорядочивается относительно других шаблонов той же категории при отображении в диалоговом окне **Создать проект** или **Добавить новый элемент**.  
  
## Синтаксис  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 `integer` представляет значение порядка сортировки.  
  
## Заметки  
 Элемент `SortOrder` является необязательным.  Значением по умолчанию является 100, все значения должны быть кратными 10.  
  
 Элемент `SortOrder` игнорируется для шаблонов, созданных пользователем.  Все шаблона, созданные пользователем, сортируются в алфавитном порядке.  
  
 Шаблоны с малыми значениями порядка сортировки отображаются в диалоговом окне **Создать проект** или **Добавить новый элемент** перед шаблонами с высокими значениями порядка сортировки.  
  
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
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 В этом примере элемент `SortOrder` обладает относительно высоким значением.  Вероятно, другие шаблоны элемента [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] будут иметь значения `SortOrder` меньше `290` и, соответственно, будут отображаться перед данным шаблоном в диалоговом окне **Создать элемент**.  
  
## См. также  
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Создание пользовательских шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)