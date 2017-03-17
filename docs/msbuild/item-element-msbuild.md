---
title: "Элемент Item (MSBuild) | Документы Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 927d80ec00ee69ca6aa59f257826307bcd3fe513
ms.lasthandoff: 03/01/2017

---
# <a name="item-element-msbuild"></a>Элемент Item (MSBuild)
Содержит определяемый пользователем элемент и его метаданные. Каждый элемент, используемый в проекте [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], должен быть указан как дочерний для элемента `ItemGroup`.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Синтаксис  

```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  

## <a name="specify-metadata-as-attributes"></a>Указание метаданных в качестве атрибутов
В MSBuild 15.1 или более поздних версиях все метаданные с именем, которое не противоречит текущему списку атрибутов, при необходимости можно выразить в виде атрибута.

Например, чтобы указать список пакетов NuGet, обычно используется примерно следующий синтаксис.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Теперь можно передать метаданные `Version` как атрибут, например как в следующем синтаксисе:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />  
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание|  
|---------------|-----------------|  
|`Include`|Обязательный атрибут.<br /><br /> Файл или подстановочный знак, включаемый в список элементов.|  
|`Exclude`|Необязательный атрибут.<br /><br /> Файл или подстановочный знак, исключаемый из списка элементов.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  
|`Remove`|Необязательный атрибут.<br /><br /> Файл или подстановочный знак, удаляемый из списка элементов.<br /><br />|  
|`KeepDuplicates`|Необязательный атрибут.<br /><br /> Указывает, следует ли добавлять элемент в целевую группу при наличии точной копией существующего элемента. Если исходный и целевой элементы имеют одинаковое значение `Include`, но различные метаданные, элемент добавляется в целевую группу, даже если `KeepDuplicates` имеет значение `false`. Дополнительные сведения см. в разделе [Элементы](../msbuild/msbuild-items.md).<br /><br /> Этот атрибут является допустимым только в том случае, если он указан для элемента `ItemGroup`, находящегося в `Target`.|  
|`KeepMetadata`|Необязательный атрибут.<br /><br /> Метаданные для исходных элементов, добавляемые в целевые элементы. Из исходного элемента в целевой передаются только метаданные, имена которых указаны в списке с разделителем точкой с запятой. Дополнительные сведения см. в разделе [Элементы](../msbuild/msbuild-items.md).<br /><br /> Этот атрибут является допустимым только в том случае, если он указан для элемента `ItemGroup`, находящегося в `Target`.|  
|`RemoveMetadata`|Необязательный атрибут.<br /><br /> Метаданные для исходных элементов, не передаваемые в целевые элементы. Из исходного элемента в целевой передаются все метаданные за исключением метаданных, имена которых содержатся в списке имен, разделенных точкой с запятой. Дополнительные сведения см. в разделе [Элементы](../msbuild/msbuild-items.md).<br /><br /> Этот атрибут является допустимым только в том случае, если он указан для элемента `ItemGroup`, находящегося в `Target`.|  
|`Update`|Необязательный атрибут. (Доступен только для проектов .NET Core в Visual Studio 2017 или более поздних версиях.)<br /><br /> Позволяет изменять метаданные файла, который был включен с помощью glob.<br /><br />  Этот атрибут является допустимым только в том случае, если он указан для элемента `ItemGroup`, не находящегося в `Target`.|  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Определяемый пользователем ключ метаданных элемента, содержащий значение метаданных элемента. Элемент может содержать любое число элементов `ItemMetadata`, включая ноль.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Группирующий элемент для элементов.|  

## <a name="remarks"></a>Примечания  
 Элементы `Item` определяют входные данные для системы построения и группируются в коллекции элементов на основании определенных пользователем имен коллекции. Эти коллекции элементов можно использовать в качестве параметров для [задач](../msbuild/msbuild-tasks.md), в которых с помощью отдельных элементов выполняются этапы процесса построения. Дополнительные сведения см. в разделе [Элементы](../msbuild/msbuild-items.md).  

 Использование нотации `@(`*myType*`)` позволяет расширить коллекцию элементов типа *myType* до списка строк, разделяемых точкой с запятой, и передать в параметр. Если параметр имеет тип `string`, значением параметра является список элементов, разделенных точкой с запятой. Если параметр представляет собой массив строк (`string[]`), каждый элемент вставляется в массив на основании расположения точек с запятой. Если параметр задачи имеет тип <xref:Microsoft.Build.Framework.ITaskItem>`[]`, значением является содержимое коллекции элементов и все присоединенные метаданные. Чтобы разделять элементы с помощью символа, отличного от точки с запятой, используйте синтаксис `@(`*myType*`, '`*разделитель*`')`.  

 Подсистема [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] может оценивать подстановочные знаки, такие как `*` и `?`, и рекурсивные подстановочные знаки, такие как `/**/*.cs`. Дополнительные сведения см. в статье [Элементы](../msbuild/msbuild-items.md).  

## <a name="examples"></a>Примеры  
 В следующем примере кода показано объявление двух элементов типа `CSFile`. Второй объявленный элемент содержит метаданные, где `MyMetadata` имеет значение `HelloWorld`.  

```xml  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
В следующем примере кода показано, как использовать `Update` атрибут для изменения метаданных в файле с именем somefile.cs, включенном с помощью glob. (Доступен только для проектов .NET Core в Visual Studio 2017 или более поздних версиях.)

```xml  
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>  
```  


## <a name="see-also"></a>См. также  
 [Элементы](../msbuild/msbuild-items.md)   
 [Свойства MSBuild](../msbuild/msbuild-properties.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)

