---
title: Элемент Property (MSBuild) | Документы Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f98e1cc8b3ce016580e477dfa648a493df1c1e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="property-element-msbuild"></a>Элемент Property (MSBuild)
Содержит определяемое пользователем имя свойства и значение. Каждое свойство, используемое в проекте [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], должно быть указано в качестве дочернего для элемента `PropertyGroup`.  

 \<Project>  
 \<PropertyGroup>  

## <a name="syntax"></a>Синтаксис  

```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Группирующий элемент для свойств.|  

## <a name="text-value"></a>Текстовое значение  
 Текстовое значение является необязательным.  

 Этот текст указывает значение свойства и может содержать XML.  

## <a name="remarks"></a>Примечания  
 Имена свойств ограничены только символами ASCII. Значения свойств указываются в проекте путем размещения имени свойства между "`$(`" и "`)`". Например, `$(builddir)\classes` разрешится в "build\classes", если свойство `builddir` будет иметь значение `build`. Дополнительные сведения о свойствах см. в статье [MSBuild Properties](../msbuild/msbuild-properties.md) (Свойства MSBuild).  

## <a name="example"></a>Пример  
 В следующем коде свойству `Optimization` задается значение `false`, а свойству `DefaultVersion` — значение `1.0`, если свойство `Version` является пустым.  

```xml  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  

## <a name="see-also"></a>См. также
[Свойства MSBuild](../msbuild/msbuild-properties.md)  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
