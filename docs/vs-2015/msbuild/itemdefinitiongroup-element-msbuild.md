---
title: Элемент ItemDefinitionGroup (MSBuild) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5aea9c7c7868dfdd9726b86bb344456ebe707d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162444"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Элемент ItemDefinitionGroup (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Элемент `ItemDefinitionGroup` позволяет определить набор определений элементов, которые представляют собой значения метаданных, по умолчанию применяемых ко всем элементам проекта. ItemDefinitionGroup заменяет необходимость использования [задачи CreateItem](../msbuild/createitem-task.md) и [задачи CreateProperty](../msbuild/createproperty-task.md). Дополнительные сведения см. в разделе [Определения элементов](../msbuild/item-definitions.md).  
  
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
|[Project](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="example"></a>Пример  
 Следующий пример кода определяет два элемента метаданных (m и n) для ItemDefinitionGroup. В этом примере к элементу i применяются метаданные по умолчанию m, так как метаданные m не определены явным образом элементом i. Однако к элементу i не применяются метаданные по умолчанию n, так как метаданные n уже определены элементом i.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)
