---
title: "Элемент ItemMetadata (MSBuild) | Microsoft Docs"
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
  - "<ItemMetadata> - элемент [MSBuild]"
  - "ItemMetadata - элемент [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Элемент ItemMetadata (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Содержит определяемый пользователем ключ метаданных элемента, содержащий значение метаданных элемента.  Элемент может иметь любое число пар ключ\-значение метаданных.  
  
## Синтаксис  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие.  Дополнительные сведения см. в разделе [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент](../msbuild/item-element-msbuild.md)|Определяемый пользователем элемент, задающий входные данные для процесса построения.|  
  
## Текстовое значение  
 Текстовое значение является необязательным.  
  
 Этот текст задает значение метаданных элемента, которые могут иметь вид текста или XML.  
  
## Заметки  
  
## Пример  
 В следующем примере кода показано, как добавить метаданные `Culture` со значением `fr` к элементу `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## См. также  
 [Справочные сведения о схеме файлов проектов](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)