---
title: "Элемент ItemDefinitionGroup (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ItemDefinitionGroup> - элемент [MSBuild]"
  - "ItemDefinitionGroup - элемент [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Элемент ItemDefinitionGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент  `ItemDefinitionGroup` позволяет определить набор определений элементов, которые являются значениями метаданных и по умолчанию применяются ко всем элементам в проекте.  Элемент ItemDefinitionGroup заменяет использование задач [Задача CreateItem](../msbuild/createitem-task.md) и [Задача CreateProperty](../msbuild/createproperty-task.md).  Дополнительные сведения см. в разделе [Определения элементов](../msbuild/item-definitions.md).  
  
## Синтаксис  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Condition`|Необязательный атрибут.  Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент](../msbuild/item-element-msbuild.md)|Входные данные для процесса построения.  Группа `ItemDefinitionGroup` может содержать ноль или более элементов `Item`.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Пример  
 В следующем примере кода в ItemDefinitionGroup определяются два элемента метаданных "m" и "n".  В этом примере к элементу "i" применяются метаданные по умолчанию "m", поскольку метаданные "m" не определены явным образом элементом "i".  Однако метаданные по умолчанию "n" не применяются к элементу "i", поскольку метаданные "n" уже определены элементом "i".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)