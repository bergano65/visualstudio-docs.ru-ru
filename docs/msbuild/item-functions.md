---
title: "Функции элементов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, Функции элементов"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
caps.handback.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Функции элементов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Начиная с MSBuild 4.0, код в задачах и целях может вызывать функции элементов для получения сведений об элементах проекта.  Эти функции упрощают получение элементов Distinct\(\) и занимают меньше времени, чем циклический просмотр всех элементов.  
  
## Функции элементов строки  
 Можно использовать методы и свойства строки в платформе .NET Framework позволяет работать с переданным ей значение элемента.  Для методов <xref:System.String> укажите имя метода.  Для свойств <xref:System.String> укажите имя свойства после "get\_".  
  
 Для элементов, имеющих несколько строк, метод строки или выполнения свойства на каждой строке.  
  
 В следующем примере показано, как использовать эти функции элемента строки.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## Встроенные функции элементов  
 Встроенные функции, доступные для элементов, перечислены в таблице ниже.  
  
|Функция|Пример|Описание|  
|-------------|------------|--------------|  
|`Count`|`@(MyItem->Count())`|Возвращает количество элементов.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Возвращает количество `Path.DirectoryName` для каждого элемента.|  
|`Distinct`|`@(MyItem->Distinct())`|Возвращает элементы, имеющие различные значения `Include`.  Метаданные игнорируются.  При сравнении регистр не учитывается.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Возвращает элементы, имеющие различные значения `itemspec`.  Метаданные игнорируются.  При сравнении учитывается регистр.|  
|`Reverse`|`@(MyItem->Reverse())`|Возвращает порядок элементов в обратном порядке.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Возвращает `boolean`, указывающее, имеет ли какой\-либо элемент заданного метаданные имя и значение.  При сравнении регистр не учитывается.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Возвращает элементы с их очищенные метаданные.  Только `itemspec` сохранятьо.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Возвращает элементы, имеющие заданное имя метаданных.  При сравнении регистр не учитывается.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Возвращает значения метаданных, которые имеют имя метаданных.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Возвращает элементы с заданными метаданными имя и значение.  При сравнении регистр не учитывается.|  
  
 В следующем примере показано, как использовать встроенные функции элемента.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## См. также  
 [Элементы](../msbuild/msbuild-items.md)