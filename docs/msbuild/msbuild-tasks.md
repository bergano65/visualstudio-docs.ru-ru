---
title: "Задачи MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
caps.latest.revision: 18
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
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: cde7cf37c372caff4faa9ec88ecc5958112f0c6f
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-tasks"></a>Задачи MSBuild
Платформе построения требуется возможность выполнения любого числа действий во время процесса построения. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] использует *задачи* для выполнения этих действий. Задача — это блок исполняемого кода, с помощью которого [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] выполняет атомарные операции построения.  
  
## <a name="task-logic"></a>Алгоритмы задач  
 Формат XML-файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] не позволяет выполнять все операции, поэтому алгоритм задачи должен быть реализован за пределами файла проекта.  
  
 Алгоритм выполнения задачи описывается в виде класса .NET, который реализует интерфейс <xref:Microsoft.Build.Framework.ITask>, определяемый в пространстве имен <xref:Microsoft.Build.Framework>.  
  
 Класс задач определяет также входные и выходные параметры, доступные задаче в файле проекта. Все открытые настраиваемые неабстрактные свойства, представляемые классом задач, описываются в файле проекта путем помещения соответствующего атрибута с тем же именем в элемент [Задача](../msbuild/task-element-msbuild.md).  
  
 Для создания собственной задачи можно разработать управляемый класс, реализующий интерфейс <xref:Microsoft.Build.Framework.ITask>. Дополнительные сведения см. в разделе [Написание задачи](../msbuild/task-writing.md).  
  
## <a name="executing-a-task-from-a-project-file"></a>Выполнение задачи из файла проекта  
 Прежде чем выполнять задачу в файле проекта, необходимо сначала сопоставить тип в сборке, которая реализует задачу, с именем задачи с элементом [UsingTask](../msbuild/usingtask-element-msbuild.md). Это позволяет [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] знать, где искать алгоритм выполнения задачи при обнаружении ее в файле проекта.  
  
 Чтобы выполнить задачу в файле проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], создайте элемент с именем таким же как у задачи в качестве дочернего элемента по отношению к элементу `Target`. Если задача принимает параметры, они передаются как атрибуты элемента.  
  
 В качестве параметров можно использовать списки элементов и свойства [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Например, следующий код вызывает задачу `MakeDir` и задает значение свойства `Directories` объекта `MakeDir` равным значению свойства `BuildDir`, объявленному в предыдущем примере.  
  
```xml  
<Target Name="MakeBuildDirectory">  
    <MakeDir  
        Directories="$(BuildDir)" />  
</Target>  
```  
  
 Задачи могут возвращать данные в файл проекта, где они могут храниться в элементах и свойствах для последующего использования. Например, следующий код вызывает задачу `Copy` и сохраняет данные из выходного свойства `CopiedFiles` в списке элементов `SuccessfullyCopiedFiles`.  
  
```xml  
<Target Name="CopyFiles">  
    <Copy  
        SourceFiles="@(MySourceFiles)"  
        DestinationFolder="@(MyDestFolder)">  
        <Output  
            TaskParameter="CopiedFiles"  
            ItemName="SuccessfullyCopiedFiles"/>  
     </Copy>  
</Target>  
```  
  
## <a name="included-tasks"></a>Включенные задачи  
 В состав [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] включено много задач, например, [Copy](../msbuild/copy-task.md) — копирование файлов, [MakeDir](../msbuild/makedir-task.md) — создание каталогов и [Csc](../msbuild/csc-task.md) — компиляция файлов исходного кода [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Полный список доступных задач и сведения об их использовании см. в разделе [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md).  
  
## <a name="overridden-tasks"></a>Переопределенные задачи  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] обнаруживает задачи в нескольких местах. Во первых, в файлах с расширением OverrideTasks, которые хранятся в каталогах .NET Framework. Задачи в этих файлах переопределяют любые другие задачи с теми же именами, в том числе задачи в файле проекта. Второе место — файлы с расширением Tasks, расположенные в каталогах .NET Framework. Если задача не найдена ни в одном из этих расположений, выполняется задача из файла проекта.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md)   
 [Написание задач](../msbuild/task-writing.md)   
 [Встроенные задачи](../msbuild/msbuild-inline-tasks.md)
