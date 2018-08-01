---
title: Элемент PropertyGroup (MSBuild) | Документы Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8c532692b7faddd90a3a67ffdd52b512511d719
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152192"
---
# <a name="propertygroup-element-msbuild"></a>Элемент PropertyGroup (MSBuild)
Содержит набор определенных пользователем элементов [Property](../msbuild/property-element-msbuild.md). Каждый элемент `Property`, используемый в проекте [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], должен быть потомком элемента `PropertyGroup`.  

 \<Project>  
 \<PropertyGroup>  

## <a name="syntax"></a>Синтаксис  

```xml  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  

## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание:|  
|---------------|-----------------|  
|Условие|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Property](../msbuild/property-element-msbuild.md)|Необязательный элемент.<br /><br /> Имя определяемого пользователем свойства, которое содержит значение свойства. Элемент `PropertyGroup` может содержать любое число элементов *Property*, включая нуль.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Проект](../msbuild/project-element-msbuild.md)|Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="example"></a>Пример  
 В следующем примере кода показано, как задать свойства на основе условия. В этом примере если свойство `CompileConfig` имеет значение `DEBUG`, задаются свойства `Optimization`, `Obfuscate` и `OutputPath` внутри элемента `PropertyGroup`.  

```xml  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  

## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)  
 [Свойства MSBuild](../msbuild/msbuild-properties.md)
