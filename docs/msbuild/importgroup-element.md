---
title: "Элемент ImportGroup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ImportGroup> - элемент [MSBuild]"
  - "ImportGroup - элемент [MSBuild]"
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Элемент ImportGroup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит коллекцию элементов `Import`, сгруппированных по дополнительное условие.  Дополнительные сведения см. в разделе [Элемент Import \(MSBuild\)](../msbuild/import-element-msbuild.md).  
  
## Синтаксис  
  
```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Импорт](../msbuild/import-element-msbuild.md)|Импорт содержимого одного файла проекта в другой файл проекта.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Заметки  
  
## Пример  
 В следующем примере показан готовый элемент `ImportGroup`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)