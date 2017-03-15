---
title: "Элемент ItemGroup (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "элемент ItemGroup [MSBuild]"
  - "элемент <ItemGroup> [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Элемент ItemGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот элемент содержит набор определяемых пользователем элементов [Item](../msbuild/item-element-msbuild.md).  Каждый элемент, используемый в проекте [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], должен быть задан как дочерний по отношению к элементу `ItemGroup`.  
  
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
|[Элемент](../msbuild/item-element-msbuild.md)|Входные данные для процесса построения.  Группа `ItemGroup` может содержать ноль или более элементов `Item`.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[Целевой объект](../msbuild/target-element-msbuild.md)|Начиная с .NET Framework версии 3.5, элемент `ItemGroup` может находиться внутри элемента `Target`.  Дополнительные сведения см. в разделе [Целевые объекты](../msbuild/msbuild-targets.md).|  
  
## Заметки  
  
## Пример  
 В следующем примере кода показаны определяемые пользователем коллекции элементов `Res` и `CodeFiles`, объявляемые внутри элемента `ItemGroup`.  В каждом элементе коллекции `Res` содержится определяемый пользователем дочерний элемент [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)   
 [Общие элементы проектов MSBuild](../msbuild/common-msbuild-project-items.md)