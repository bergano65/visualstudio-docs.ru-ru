---
title: Элемент ItemMetadata (MSBuild) | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 64786e5066476fcaca161fe0511f97a1fd2c7fd6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917531"
---
# <a name="itemmetadata-element-msbuild"></a>Элемент ItemMetadata (MSBuild)
Содержит определяемый пользователем ключ метаданных элемента, содержащий значение метаданных элемента. Элемент может иметь любое число пар метаданных "ключ — значение".  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Синтаксис  

```xml  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент](../msbuild/item-element-msbuild.md)|Определяемый пользователем элемент, задающий входные данные для процесса сборки.|  

## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является необязательным.  

 Этот текст задает для элемента значение метаданных, которое может быть текстом или XML-документом.  

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
