---
title: Элементы MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, Items
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d517d3fd24b17c33a7bba9f888fbb904631be5f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851937"
---
# <a name="msbuild-items"></a>Элементы MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Элементы MSBuild — это входные данные для системы сборки. Они, обычно, представляют файлы. Элементы группируются в типы, определяемые их именами. Типы элементов — это именованные списки элементов, которые можно использовать в качестве параметров для задач. Задачи используют значения элементов для выполнения этапов процесса сборки.  
  
 Так как имена элементов образуются от имен типов, которым они принадлежат, термины "элемент" и "значение элемента" могут использоваться один вместо другого.  
  
 **Содержание раздела**  
  
-   [Создание элементов в файле проекта](#BKMK_Creating1)  
  
-   [Создание элементов во время выполнения](#BKMK_Creating2)  
  
-   [Ссылки на элементы в файле проекта](#BKMK_ReferencingItems)  
  
-   [Использование подстановочных знаков для указания элементов](#BKMK_Wildcards)  
  
-   [Использование атрибута Exclude](#BKMK_ExcludeAttribute)  
  
-   [Метаданные элементов](#BKMK_ItemMetadata)  
  
    -   [Ссылки на метаданные элементов в файле проекта](#BKMK_ReferencingItemMetadata)  
  
    -   [Стандартные метаданные элементов](#BKMK_WellKnownItemMetadata)  
  
    -   [Преобразование типов элементов с помощью метаданных](#BKMK_Transforming)  
  
-   [Определения элементов](#BKMK_ItemDefinitions)  
  
-   [Атрибуты элементов в элементе ItemGroup целевого объекта](#BKMK_AttributesWithinTargets)  
  
    -   [Удаление атрибута](#BKMK_RemoveAttribute)  
  
    -   [Атрибут KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Атрибут RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Атрибут KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="BKMK_Creating1"></a> Создание элементов в файле проекта  
 Элементы в файле проекта объявляются как дочерние элементы элемента [ItemGroup](../msbuild/itemgroup-element-msbuild.md). Имя дочернего элемента совпадает с именем типа элемента. Атрибут `Include` элемента определяет элементы (файлы), которые следует включить в данный тип элементов. В приведенном ниже примере XML-кода создается тип элементов с именем `Compile`, в который входят два файла.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Элемент "file2.cs" не заменяет собой элемент "file1.cs". Имя файла добавляется в список значений для типа элемента `Compile`. Удалить элемент из типа элементов на этапе оценки сборки нельзя.  
  
 Следующий XML-код создает такой же тип элементов путем объявления обоих файлов в одном атрибуте `Include`. Обратите внимание, что имена файлов разделяются точкой с запятой.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="BKMK_Creating2"></a> Создание элементов во время выполнения  
 Значения элементам, находящимся за пределами элементов [Target](../msbuild/target-element-msbuild.md), присваиваются на этапе оценки сборки. На следующем этапе выполнения элементы могут быть созданы и их значения могут быть изменены следующим образом.  
  
-   Любая задача может создать элемент. Для создания элемента элемент [Задача](../msbuild/task-element-msbuild.md) должен иметь дочерний элемент [Выходные данные](../msbuild/output-element-msbuild.md) с атрибутом `ItemName`.  
  
-   Задача [CreateItem](../msbuild/createitem-task.md) также может создать элемент. Этот способ не рекомендуется использовать.  
  
-   Начиная с версии .NET Framework 3.5, элементы `Target` могут содержать элементы [ItemGroup](../msbuild/itemgroup-element-msbuild.md), которые могут содержать элементы Item.  
  
##  <a name="BKMK_ReferencingItems"></a> Ссылки на элементы в файле проекта  
 Для обращения к типам элементов в файле проекта используется синтаксис @(`ItemType`). Например, для обращения к типу элементов из предыдущего примера следует использовать конструкцию `@(Compile)`. Используя этот синтаксис, можно передавать элементы в задачи, указывая тип элементов в качестве параметра этой задачи. Дополнительные сведения см. в разделе [Практическое руководство. Выбор файлов для сборки](../msbuild/how-to-select-the-files-to-build.md).  
  
 По умолчанию при развертывании элементы типа разделяются знаком "точка с запятой" (;). Чтобы указать другой разделитель, используйте синтаксис @(*ItemType*, "*разделитель*"). Дополнительные сведения см. в разделе [Практическое руководство. Отображение списка элементов, разделенных запятыми](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="BKMK_Wildcards"></a> Использование подстановочных знаков для указания элементов  
 Для указания групп файлов можно использовать подстановочные знаки **, \*, и ?. С помощью этих знаков можно указать сразу группу файлов в качестве входных данных для сборки, вместо того, чтобы перечислять эти файлы каждый по отдельности.  
  
- Подстановочный знак ? заменяет один символ.  
  
- Знак * заменяет несколько символов (или ни одного).  
  
- Последовательность подстановочных знаков ** заменяет частичный путь.  
  
  Например, можно указать все CS-файлы в каталоге с файлом проекта, используя следующий элемент в файле проекта.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Следующий элемент выбирает всех VB-файлы на диске D.  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Дополнительные сведения о подстановочных знаках см. в разделе [Практическое руководство. Выбор файлов для сборки](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="BKMK_ExcludeAttribute"></a> Использование атрибута Exclude  
 Элементы Item могут содержать атрибут `Exclude`, исключающий определенные элементы (файлы) из типа элементов. Атрибут `Exclude` обычно используется вместе с подстановочными знаками. Следующий пример XML-кода добавляет все CS-файлы, которые есть в каталоге, в тип элементов CSFile, за исключением файла `DoNotBuild.cs`.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
 Атрибут `Exclude` применяется только к элементам, добавляемым с помощью атрибута `Include` в элемент Item, содержащий их оба. В следующем примере файл Form1.cs, добавленный в предыдущий элемент Item, не исключается.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Дополнительные сведения см. в разделе [Практическое руководство. Исключение файлов из сборки](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="BKMK_ItemMetadata"></a> Метаданные элементов  
 Помимо сведений в атрибутах `Include` и `Exclude` элементы могут содержать метаданные. Эти метаданные могут использоваться задачами, требующими дополнительных сведений об элементах, или для пакетной обработки задач и целевых объектов. Дополнительные сведения см. в разделе [Пакетная обработка](../msbuild/msbuild-batching.md).  
  
 Метаданные — это коллекция пар "ключ-значение", которые объявляются в файле проекта как дочерние элементы элемента Item. Имя дочернего элемента совпадает с именем метаданных, а значение дочернего элемента совпадает со значением метаданных.  
  
 Метаданные связаны с элементом Item, который их содержит. Следующий пример XML-кода добавляет метаданные `Culture`, имеющие значение `Fr`, в оба элемента "one.cs" и "two.cs", принадлежащие типу CSFile.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Элемент может содержать несколько значений метаданных (или ни одного). Значения метаданных можно изменить в любое время. Если задать для метаданных пустое значение, это фактически будет означать их удаление из сборки.  
  
###  <a name="BKMK_ReferencingItemMetadata"></a> Ссылки на метаданные элементов в файле проекта  
 Для обращения к метаданным элемента в файле проекта используется синтаксис %(`ItemMetadataName`). Если возникает неоднозначность, можно ограничить применение ссылки с помощью имени типа элемента. Например, можно указать %(*ItemType.ItemMetaDataName*). В следующем примере метаданные Display используются для пакетной обработки задачи Message. Дополнительные сведения об использовании метаданных элементов для пакетной обработки см. в разделе [Метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Stuff Include="One.cs" >  
            <Display>false</Display>  
        </Stuff>  
        <Stuff Include="Two.cs">  
            <Display>true</Display>  
        </Stuff>  
    </ItemGroup>  
    <Target Name="Batching">  
        <Message Text="@(Stuff)" Condition=" '%(Display)' == 'true' "/>  
    </Target>  
</Project>  
```  
  
###  <a name="BKMK_WellKnownItemMetadata"></a> Стандартные метаданные элементов  
 Когда элемент добавляется в тип элементов, ему назначаются некоторые стандартные метаданные. Например, все элементы имеют стандартные метаданные `%(Filename)`. В этом случае значением является имя файла элемента. Дополнительные сведения см. в разделе [Стандартные метаданные элементов](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="BKMK_Transforming"></a> Преобразование типов элементов с помощью метаданных  
 С помощью метаданных можно преобразовать списки элементов в новые списки элементов. Например, можно преобразовать тип элемента `CppFiles`, содержащий элементы, представляющие CPP-файлы, в соответствующий список OBJ-файлов с помощью выражения `@(CppFiles -> '%(Filename).obj')`.  
  
 Следующий код создает тип `CultureResource`, содержащий копии всех элементов `EmbeddedResource` с метаданными `Culture`. Значения метаданных `Culture` присваиваются новым метаданным `CultureResource.TargetDirectory`.  
  
```  
<Target Name="ProcessCultureResources">  
    <ItemGroup>  
        <CultureResource Include="@(EmbeddedResource)"  
            Condition="'%(EmbeddedResource.Culture)' != ''">  
            <TargetDirectory>%(EmbeddedResource.Culture) </TargetDirectory>  
        </CultureResource>  
    </ItemGroup>  
</Target>  
```  
  
 Дополнительные сведения см. в статье [Преобразования](../msbuild/msbuild-transforms.md).  
  
##  <a name="BKMK_ItemDefinitions"></a> Определения элементов  
 Начиная с версии .NET Framework 3.5, добавить метаданные по умолчанию в любой тип элементов можно с помощью [элемента ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Подобно стандартным метаданным, метаданные по умолчанию связаны со всеми элементами указанного типа. Метаданные по умолчанию можно в явном виде переопределить в определении элемента. В следующем примере XML-кода элементам `Compile` "one.cs" и "three.cs" назначаются метаданные `BuildDay` со значением "Понедельник". В этом коде элементу two.cs назначаются метаданные `BuildDay` со значением "Вторник".  
  
```  
<ItemDefinitionGroup>  
    <Compile>  
        <BuildDay>Monday</BuildDay>  
    </Compile>  
</ItemDefinitionGroup>  
<ItemGroup>  
    <Compile Include="one.cs;three.cs" />  
    <Compile Include="two.cs">  
        <BuildDay>Tuesday</BuildDay>  
    </Compile>  
</ItemGroup>  
```  
  
 Дополнительные сведения см. в разделе [Определения элементов](../msbuild/item-definitions.md).  
  
##  <a name="BKMK_AttributesWithinTargets"></a> Атрибуты элементов в элементе ItemGroup целевого объекта  
 Начиная с версии .NET Framework 3.5, элементы `Target` могут содержать элементы [ItemGroup](../msbuild/itemgroup-element-msbuild.md), которые могут содержать элементы Item. Атрибуты в этом разделе допустимы, если они указаны для элемента в `ItemGroup`, который находится в `Target`.  
  
###  <a name="BKMK_RemoveAttribute"></a> Удаление атрибута  
 Элементы в элементе `ItemGroup` целевого объекта могут содержать атрибут `Remove`, задающий удаление определенных элементов (файлов) из типа элементов. Этот атрибут появился в .NET Framework версии 3.5.  
  
 В следующем примере удаляются все файлы с расширением CONFIG из типа элемента Compile.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="BKMK_KeepMetadata"></a> Атрибут KeepMetadata  
 Если элемент создается в целевом объекте, элемент Item может содержать атрибут `KeepMetadata`. Если этот атрибут задан, из исходного элемента в целевой передаются только те метаданные, имена которых содержатся в списке имен, разделенных точкой с запятой. Пустое значение этого атрибута эквивалентно тому, что атрибут не задан. Атрибут `KeepMetadata` появился в .NET Framework версии 4.5.  
  
 В следующем примере показано использование атрибута `KeepMetadata`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0">  
  
    <ItemGroup>  
        <FirstItem Include="rhinoceros">  
            <Class>mammal</Class>  
            <Size>large</Size>  
        </FirstItem>  
  
    </ItemGroup>  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <SecondItem Include="@(FirstItem)" KeepMetadata="Class" />  
        </ItemGroup>  
  
        <Message Text="FirstItem: %(FirstItem.Identity)" />  
        <Message Text="  Class: %(FirstItem.Class)" />  
        <Message Text="  Size:  %(FirstItem.Size)"  />  
  
        <Message Text="SecondItem: %(SecondItem.Identity)" />  
        <Message Text="  Class: %(SecondItem.Class)" />  
        <Message Text="  Size:  %(SecondItem.Size)"  />  
    </Target>  
</Project>  
  
<!--  
Output:  
  FirstItem: rhinoceros  
    Class: mammal  
    Size:  large  
  SecondItem: rhinoceros  
    Class: mammal  
    Size:   
-->  
```  
  
###  <a name="BKMK_RemoveMetadata"></a> Атрибут RemoveMetadata  
 Если элемент создается в целевом объекте, элемент Item может содержать атрибут `RemoveMetadata`. Если этот атрибут задан, из исходного элемента в целевой передаются все метаданные за исключением метаданных, имена которых содержатся в списке имен, разделенных точкой с запятой. Пустое значение этого атрибута эквивалентно тому, что атрибут не задан. Атрибут `RemoveMetadata` появился в .NET Framework версии 4.5.  
  
 В следующем примере показано использование атрибута `RemoveMetadata`.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <MetadataToRemove>Size;Material</MetadataToRemove>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <Item1 Include="stapler">  
            <Size>medium</Size>  
            <Color>black</Color>  
            <Material>plastic</Material>  
        </Item1>  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item2 Include="@(Item1)" RemoveMetadata="$(MetadataToRemove)" />  
        </ItemGroup>  
  
        <Message Text="Item1: %(Item1.Identity)" />  
        <Message Text="  Size:     %(Item1.Size)" />  
        <Message Text="  Color:    %(Item1.Color)" />  
        <Message Text="  Material: %(Item1.Material)" />  
        <Message Text="Item2: %(Item2.Identity)" />  
        <Message Text="  Size:     %(Item2.Size)" />  
        <Message Text="  Color:    %(Item2.Color)" />  
        <Message Text="  Material: %(Item2.Material)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: stapler  
    Size:     medium  
    Color:    black  
    Material: plastic  
  Item2: stapler  
    Size:       
    Color:    black  
    Material:   
-->  
```  
  
###  <a name="BKMK_KeepDuplicates"></a> Атрибут KeepDuplicates  
 Если элемент создается в целевом объекте, элемент Item может содержать атрибут `KeepDuplicates`. `KeepDuplicates` — это атрибут `Boolean`, который указывает, следует ли добавлять элемент в целевую группу, если он является точной копией существующего элемента.  
  
 Если исходный и целевой элементы имеют одинаковые значения Include, но разные метаданные, элемент добавляется в целевую группу, даже если `KeepDuplicates` имеет значение `false`. Пустое значение этого атрибута эквивалентно тому, что атрибут не задан. Атрибут `KeepDuplicates` появился в .NET Framework версии 4.5.  
  
 В следующем примере показано использование атрибута `KeepDuplicates`.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Item1 Include="hourglass;boomerang" />  
        <Item2 Include="hourglass;boomerang" />  
    </ItemGroup>  
  
    <Target Name="MyTarget">  
        <ItemGroup>  
            <Item1 Include="hourglass" KeepDuplicates="false" />  
            <Item2 Include="hourglass" />  
        </ItemGroup>  
  
        <Message Text="Item1: @(Item1)" />  
        <Message Text="  %(Item1.Identity)  Count: @(Item1->Count())" />  
        <Message Text="Item2: @(Item2)" />  
        <Message Text="  %(Item2.Identity)  Count: @(Item2->Count())" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Item1: hourglass;boomerang  
    hourglass  Count: 1  
    boomerang  Count: 1  
  Item2: hourglass;boomerang;hourglass  
    hourglass  Count: 2  
    boomerang  Count: 1  
-->  
```  
  
## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)   
 [Практическое руководство. Выбор файлов для сборки](../msbuild/how-to-select-the-files-to-build.md)   
 [Практическое руководство. Исключение файлов из сборки](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Практическое руководство. Отображение списка элементов, разделенных запятыми](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Определения элементов](../msbuild/item-definitions.md)   
 [Пакетная обработка](../msbuild/msbuild-batching.md)   
 [Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md)


