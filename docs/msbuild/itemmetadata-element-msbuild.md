---
title: "Элемент ItemMetadata (MSBuild) | Документация Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72c6b65991eb90d71856b33398ff2b42f6fcb377
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="itemmetadata-element-msbuild"></a>Элемент ItemMetadata (MSBuild)
Содержит определяемый пользователем ключ метаданных элемента, содержащий значение метаданных элемента. Элемент может иметь любое число пар метаданных "ключ — значение".  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Синтаксис  

```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание:|  
|---------------|-----------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент](../msbuild/item-element-msbuild.md)|Определяемый пользователем элемент, задающий входные данные для процесса сборки.|  

## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является необязательным.  

 Этот текст задает для элемента значение метаданных, которое может быть текстом или XML-документом.  

## <a name="remarks"></a>Примечания  

## <a name="example"></a>Пример  
 Следующий пример кода демонстрирует добавление метаданных `Culture` со значением `fr` к элементу `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)
