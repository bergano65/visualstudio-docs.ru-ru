---
title: "Элементы MSBuild | Microsoft Docs"
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
  - "Элементы MSBuild"
ms.assetid: d762eff4-c92a-4b5f-a944-1ca30aa22319
caps.latest.revision: 35
caps.handback.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Элементы MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элементы MSBuild являются входными данными для системы построения, и они обычно представляют собой файлы. Элементы группируются в типы на основе своих имен элемента. Типы элементов являются именованными списками элементов, которые можно использовать в качестве параметров для задач. Задачи используют значения элементов выполняются этапы процесса построения.  
  
 Поскольку имена элементов по типу элемента, к которому они принадлежат, термины «item» и «значение элемента» взаимозаменяемы.  
  
 **В этом разделе**  
  
-   [Создание элементов в файле проекта](#BKMK_Creating1)  
  
-   [Создание элементов во время выполнения](#BKMK_Creating2)  
  
-   [Ссылки на элементы в файл проекта](#BKMK_ReferencingItems)  
  
-   [Использование подстановочных знаков для указания элементов](#BKMK_Wildcards)  
  
-   [С помощью атрибута Exclude](#BKMK_ExcludeAttribute)  
  
-   [Метаданные элементов](#BKMK_ItemMetadata)  
  
    -   [Ссылки на метаданные элементов в файле проекта](#BKMK_ReferencingItemMetadata)  
  
    -   [Общеизвестные метаданные элементов](#BKMK_WellKnownItemMetadata)  
  
    -   [Преобразование типов элементов с помощью метаданных](#BKMK_Transforming)  
  
-   [Определения элементов](#BKMK_ItemDefinitions)  
  
-   [Атрибуты для элементов в ItemGroup целевой базы данных](#BKMK_AttributesWithinTargets)  
  
    -   [Удаление атрибута](#BKMK_RemoveAttribute)  
  
    -   [Атрибут KeepMetadata](#BKMK_KeepMetadata)  
  
    -   [Атрибут RemoveMetadata](#BKMK_RemoveMetadata)  
  
    -   [Атрибут KeepDuplicates](#BKMK_KeepDuplicates)  
  
##  <a name="a-namebkmkcreating1a-creating-items-in-a-project-file"></a><a name="BKMK_Creating1"></a> Создание элементов в файле проекта  
 Необходимо обозначить элементы в файле проекта как дочерние элементы [ItemGroup](../msbuild/itemgroup-element-msbuild.md) элемента. Имя дочернего элемента является типом элемента.  `Include` Атрибута элемента указывает элементы (файлы), которые нужно включить в данный тип элементов. Например, следующий XML-КОД создается тип элементов с именем `Compile`, который входят два файла.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Элемент «file2.cs» не заменяет элемент «file1.cs»; Вместо этого имени файла добавляется в список значений для `Compile` тип элемента. Не удается удалить элемент из типа элементов на этапе оценки построения.  
  
 Следующий XML-КОД тот же тип элементов создается посредством объявления обоих файлов в одном `Include` атрибута. Обратите внимание, что имена файлов разделяются точкой с запятой.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs;file2.cs"/>  
</ItemGroup>  
```  
  
##  <a name="a-namebkmkcreating2a-creating-items-during-execution"></a><a name="BKMK_Creating2"></a> Создание элементов во время выполнения  
 Элементы, которые находятся за пределами [целевой](../msbuild/target-element-msbuild.md) элементы, значения присваиваются на этапе оценки построения. На этапе выполнения элементов может быть создано или изменено следующими способами:  
  
-   Любая задача может создавать элемент. Для этого элемент [задачи](../msbuild/task-element-msbuild.md) элемент должен иметь дочерний [вывода](../msbuild/output-element-msbuild.md) элемент, имеющий `ItemName` атрибута.  
  
-    [CreateItem](../msbuild/createitem-task.md) Задача может отправить элемент. Этот метод рекомендуется использовать.  
  
-   Начиная с .NET Framework 3.5, `Target` элементы могут содержать [ItemGroup](../msbuild/itemgroup-element-msbuild.md) элементы, которые могут содержать элемент элементы.  
  
##  <a name="a-namebkmkreferencingitemsa-referencing-items-in-a-project-file"></a><a name="BKMK_ReferencingItems"></a> Ссылки на элементы в файл проекта  
 Для ссылки на типы элементов в файле проекта используется синтаксис @(`ItemType`). Например, тип элементов в предыдущем примере будет ссылаться с помощью `@(Compile)`. С помощью следующего синтаксиса, можно передавать элементы задачи, указав тип элементов в качестве параметра этой задачи. Дополнительные сведения см. в разделе [как: выберите файлы для построения](../msbuild/how-to-select-the-files-to-build.md).  
  
 По умолчанию элементы типа элементов разделяются точками с запятой (;), при ее развертывании. Можно использовать синтаксис @(*ItemType*, "*разделителя*"), чтобы указать разделитель, используемый по умолчанию. Дополнительные сведения см. в разделе [как: отображения элементов списка разделенных запятыми](../msbuild/how-to-display-an-item-list-separated-with-commas.md).  
  
##  <a name="a-namebkmkwildcardsa-using-wildcards-to-specify-items"></a><a name="BKMK_Wildcards"></a> Использование подстановочных знаков для указания элементов  
 Можно использовать **, \*, а? подстановочные знаки, чтобы указать группу файлов в качестве входных данных для построения вместо перечисления каждого файла по отдельности.  
  
-   ? символ-шаблон соответствует один символ.  
  
-   * Символ-шаблон соответствует нулю или нескольким символам.  
  
-   ** Последовательность подстановочных знаков соответствует частичный путь.  
  
 Например можно указать CS-файлов в каталоге с файлом проекта с помощью следующего элемента в файле проекта.  
  
```  
<CSFile Include="*.cs"/>  
```  
  
 Следующий элемент выбирает всех VB-файлов на диске D:.  
  
```  
<VBFile Include="D:/**/*.vb"/>  
```  
  
 Дополнительные сведения о подстановочных знаках см. в разделе [как: выберите файлы для построения](../msbuild/how-to-select-the-files-to-build.md).  
  
##  <a name="a-namebkmkexcludeattributea-using-the-exclude-attribute"></a><a name="BKMK_ExcludeAttribute"></a> С помощью атрибута Exclude  
 Элементы могут содержать `Exclude` атрибут, исключающий определенные элементы (файлы) из типа элементов.  `Exclude` Атрибут обычно используется вместе с подстановочными знаками. Например, следующий XML-КОД добавляет каждый CS-файл в каталоге в тип элементов CSFile, за исключением `DoNotBuild.cs` файла.  
  
```  
<ItemGroup>  
    <CSFile  Include="*.cs"  Exclude="DoNotBuild.cs"/>  
</ItemGroup>  
```  
  
  `Exclude` Атрибут влияет только элементы, которые были добавлены с `Include` атрибут в элемент, содержащий оба этих. Следующий пример не исключить файл Form1.cs, добавленный в предыдущем элементе.  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 Дополнительные сведения см. в разделе [как: Исключить файлы из сборки](../msbuild/how-to-exclude-files-from-the-build.md).  
  
##  <a name="a-namebkmkitemmetadataa-item-metadata"></a><a name="BKMK_ItemMetadata"></a> Метаданные элементов  
 Элементы могут содержать метаданные, кроме сведений в `Include` и `Exclude` атрибуты. Эти метаданные могут использоваться задачи, которые требуют дополнительных сведений об элементах или пакетной обработки задач и целевых объектов. Дополнительные сведения см. в разделе [Пакетная обработка](../msbuild/msbuild-batching.md).  
  
 Метаданные является коллекцией пар "ключ значение", объявленных в файле проекта как дочерние элементы элемента. Имя дочернего элемента является имя метаданных, и значение дочернего элемента — значение метаданных.  
  
 Метаданные связан с элемента, который его содержит. Например, следующий XML-КОД добавляет `Culture` метаданные, имеющие значение `Fr` «one.cs» и «two.cs» элементов CSFile тип элемента.  
  
```  
<ItemGroup>  
    <CSFile Include="one.cs;two.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Элемент может содержать ноль или более значений метаданных. Значения метаданных можно изменить в любое время. Если задать метаданные в пустое значение, он фактически удалить из построения.  
  
###  <a name="a-namebkmkreferencingitemmetadataa-referencing-item-metadata-in-a-project-file"></a><a name="BKMK_ReferencingItemMetadata"></a> Ссылки на метаданные элементов в файле проекта  
 Можно ссылки на метаданные элементов в файле проекта используется синтаксис %(`ItemMetadataName`). Если существует неоднозначность, можно определить ссылку с помощью имени типа элемента. Например, можно указать %(*ItemType.ItemMetaDataName*). В следующем примере метаданные Display для пакетной обработки задачи Message. Дополнительные сведения об использовании метаданных элементов для пакетной обработки см. в разделе [метаданные элементов в пакетной обработке задач](../msbuild/item-metadata-in-task-batching.md).  
  
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
  
###  <a name="a-namebkmkwellknownitemmetadataa-well-known-item-metadata"></a><a name="BKMK_WellKnownItemMetadata"></a> Общеизвестные метаданные элементов  
 При добавлении элемента к типу элементов этого элемента назначается некоторые стандартные метаданные. Например, все элементы имеют хорошо известных метаданных `%(Filename)`, значением которого является имя файла элемента. Дополнительные сведения см. в разделе [Общеизвестные метаданные элементов](../msbuild/msbuild-well-known-item-metadata.md).  
  
###  <a name="a-namebkmktransforminga-transforming-item-types-by-using-metadata"></a><a name="BKMK_Transforming"></a> Преобразование типов элементов с помощью метаданных  
 Списки элементов можно преобразовать в новые списки элементов с помощью метаданных. Например, можно преобразовать тип элемента `CppFiles` содержащий элементы, представляющие CPP-файлы в соответствующий список OBJ-файлов с помощью выражения `@(CppFiles -> '%(Filename).obj')`.  
  
 Следующий код создает `CultureResource` тип, содержащий все копии элемента `EmbeddedResource` элементы с `Culture` метаданных.  `Culture` Метаданных присваивается значение новых метаданных `CultureResource.TargetDirectory`.  
  
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
  
 Дополнительные сведения см. в разделе [преобразует](../msbuild/msbuild-transforms.md).  
  
##  <a name="a-namebkmkitemdefinitionsa-item-definitions"></a><a name="BKMK_ItemDefinitions"></a> Определения элементов  
 Начиная с .NET Framework 3.5, добавляются метаданные по умолчанию для любого типа элемента с помощью [элемент ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md). Подобно стандартным метаданным метаданные по умолчанию связываются со всеми элементами указанного типа элемента. Можно явно переопределить метаданные по умолчанию в определении элемента. Например, следующий код XML дает `Compile` элементы «one.cs» и «three.cs» метаданные `BuildDay` со значением «Понедельник». Код предоставляет элемент «two.cs» метаданные `BuildDay` со значением «Вторник».  
  
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
  
 Дополнительные сведения см. в разделе [определений элементов](../msbuild/item-definitions.md).  
  
##  <a name="a-namebkmkattributeswithintargetsa-attributes-for-items-in-an-itemgroup-of-a-target"></a><a name="BKMK_AttributesWithinTargets"></a> Атрибуты для элементов в ItemGroup целевой базы данных  
 Начиная с .NET Framework 3.5, `Target` элементы могут содержать [ItemGroup](../msbuild/itemgroup-element-msbuild.md) элементы, которые могут содержать элемент элементы. Атрибуты в этом разделе, допустимы, если они указаны для элемента `ItemGroup` в `Target`.  
  
###  <a name="a-namebkmkremoveattributea-remove-attribute"></a><a name="BKMK_RemoveAttribute"></a> Удаление атрибута  
 Элементы в `ItemGroup` целевой базы данных может содержать `Remove` атрибут, который удаляет определенные элементы (файлы) из типа элементов. Этот атрибут был введен в .NET Framework 3.5.  
  
 В следующем примере удаляется каждый файл .config на основе типа элемента компиляции.  
  
```  
<Target>  
    <ItemGroup>  
        <Compile Remove="*.config"/>  
    </ItemGroup>  
</Target>  
```  
  
###  <a name="a-namebkmkkeepmetadataa-keepmetadata-attribute"></a><a name="BKMK_KeepMetadata"></a> Атрибут KeepMetadata  
 Если элемент создается в целевой объект, элемент может содержать `KeepMetadata` атрибута. Если этот атрибут указан, только метаданные, указанные в разделенных точкой с запятой список имен будут перенесены из исходного элемента в целевой элемент. Соответствует пустое значение для этого атрибута не указано.  `KeepMetadata` Появился в платформе .NET Framework 4.5.  
  
 Следующий пример иллюстрирует использование `KeepMetadata` атрибута.  
  
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
  
###  <a name="a-namebkmkremovemetadataa-removemetadata-attribute"></a><a name="BKMK_RemoveMetadata"></a> Атрибут RemoveMetadata  
 Если элемент создается в целевой объект, элемент может содержать `RemoveMetadata` атрибута. Если этот атрибут указан, все метаданные передается из исходного элемента целевого элемента, за исключением метаданных, имена которых содержатся в списке имена, разделенных точкой с запятой. Соответствует пустое значение для этого атрибута не указано.  `RemoveMetadata` Появился в платформе .NET Framework 4.5.  
  
 Следующий пример иллюстрирует использование `RemoveMetadata` атрибута.  
  
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
  
###  <a name="a-namebkmkkeepduplicatesa-keepduplicates-attribute"></a><a name="BKMK_KeepDuplicates"></a> Атрибут KeepDuplicates  
 Если элемент создается в целевой объект, элемент может содержать `KeepDuplicates` атрибута. `KeepDuplicates` — `Boolean` атрибут, указывающий, следует ли добавлять элемент в целевую группу, если элемент является точной копией существующего элемента.  
  
 Если исходной и целевой элемент имеет то же значение Include, но различные метаданные, элемент добавляется даже в том случае, если `KeepDuplicates` имеет значение `false`. Соответствует пустое значение для этого атрибута не указано.  `KeepDuplicates` Появился в платформе .NET Framework 4.5.  
  
 Следующий пример иллюстрирует использование `KeepDuplicates` атрибута.  
  
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
  
## <a name="see-also"></a>См. также раздел  
 [Основные возможности MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)   
 [Практическое руководство: Выбор файлов для сборки](../msbuild/how-to-select-the-files-to-build.md)   
 [Практическое руководство: исключение файлов из построения](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Практическое руководство: Отображение списка элементов, разделенных запятыми](../msbuild/how-to-display-an-item-list-separated-with-commas.md)   
 [Определения элементов](../msbuild/item-definitions.md)   
 [Пакетная обработка](../msbuild/msbuild-batching.md)   
 [Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md)