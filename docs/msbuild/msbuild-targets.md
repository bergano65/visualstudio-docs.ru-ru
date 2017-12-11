---
title: "Целевые объекты MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: "26"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 29c9397ea886024c894b977f05ec83f8d7c70f60
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-targets"></a>Цели MSBuild
Целевые объекты позволяют группировать задачи в определенном порядке, а также разложить процесс сборки на более мелкие этапы. Например, один целевой объект может удалить все файлы в выходном каталоге для подготовки к сборке, пока другой компилирует входные данные для проекта и помещает их в пустой каталог. Дополнительные сведения о задачах см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Объявление целевых объектов в файле проекта  
 Целевые объекты объявляются в файле проекта с помощью элемента [Target](../msbuild/target-element-msbuild.md). Например, следующий XML-код создает целевой объект с именем Construct, который затем вызывает задачу Csc с типом элемента Compile.  
  
```xml  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Как и свойства MSBuild, целевые объекты можно переопределить. Например:  
  
```xml  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Если выполняется AfterBuild, он отображает только "второе вхождение".  
  
## <a name="target-build-order"></a>Порядок построения целевого объекта  
 Целевые объекты необходимо упорядочить, если входные данные для одного целевого объекта зависят от выходных данных другого целевого объекта. Есть несколько способов, чтобы указать порядок выполнения целевых объектов.  
  
-   Начальные целевые объекты  
  
-   Целевые объекты по умолчанию  
  
-   Первый целевой объект  
  
-   Зависимости целевого объекта  
  
-   `BeforeTargets` и `AfterTargets` (MSBuild 4.0)  
  
 Целевой объект никогда не выполняется дважды во время одной сборки, даже если от него зависит последующий целевой объект в сборке. После запуска целевого объекта его участие в сборке завершается.  
  
 Дополнительные сведения о порядке сборки целевых объектов см. в разделе [Порядок построения целевого объекта](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Пакетная обработка целевых объектов  
 Целевой элемент может иметь атрибут `Outputs`, который указывает метаданные в формате %(Metadata). В этом случае MSBuild запускает целевой объект один раз для каждого уникального значения метаданных, группируя или "пакетно обрабатывая" элементы, имеющие это значение метаданных. Например:  
  
```xml  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 пакетно обрабатывает элементы Reference по их метаданным RequiredTargetFramework. Выходные данные этого целевого объекта выглядят следующим образом:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 В реальных сборках пакетная обработка целевых объектов используется редко. Больше распространена пакетная обработка задач. Дополнительные сведения см. в статье [Пакетная обработка](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Инкрементные построения  
 Инкрементные сборки — это сборки, оптимизированные таким образом, чтобы целевые объекты с выходными файлами, которые актуальны в отношении соответствующих входных файлов, не выполнялись. Целевой элемент может иметь оба атрибута `Inputs` и `Outputs`, указывая, какие элементы целевой объект ожидает в качестве входных данных и какие элементы создает в качестве выходных.  
  
 Если все выходные элементы актуальны, MSBuild пропускает этот целевой объект, что значительно ускоряет сборку. Это называется инкрементной сборкой целевого объекта. Если актуальны лишь некоторые файлы, MSBuild выполняет целевой объект без актуальных элементов. Это называется частичной инкрементной сборкой целевого объекта. Дополнительные сведения см. в разделе [Инкрементные сборки](../msbuild/incremental-builds.md).  
  
## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [Как использовать одинаковый целевой объект в нескольких файлах проектов](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)