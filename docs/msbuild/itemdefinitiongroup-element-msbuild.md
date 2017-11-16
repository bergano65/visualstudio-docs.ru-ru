---
title: "Элемент ItemDefinitionGroup (MSBuild) | Документация Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7f3ce1114f1f1b071e928128e3fea85f6a69c62a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Элемент ItemDefinitionGroup (MSBuild)
Элемент `ItemDefinitionGroup` позволяет определить набор определений элементов, которые представляют собой значения метаданных, по умолчанию применяемых ко всем элементам проекта. ItemDefinitionGroup пришел на смену использованию [задач CreateItem](../msbuild/createitem-task.md) и [задач CreateProperty](../msbuild/createproperty-task.md). Дополнительные сведения см. в разделе [Определения элементов](../msbuild/item-definitions.md).  

 \<Project>  
 \<ItemDefinitionGroup>  

## <a name="syntax"></a>Синтаксис  

```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный атрибут. Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент](../msbuild/item-element-msbuild.md)|Входные данные для процесса сборки. Любое количество элементов `Item` (может быть ни одного) может содержаться в `ItemDefinitionGroup`.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="example"></a>Пример  
 Следующий пример кода определяет два элемента метаданных (m и n) для ItemDefinitionGroup. В этом примере к элементу i применяются метаданные по умолчанию m, так как метаданные m не определены явным образом элементом i. Однако к элементу i не применяются метаданные по умолчанию n, так как метаданные n уже определены элементом i.  

```xml  
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

## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)
