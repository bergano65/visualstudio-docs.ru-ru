---
title: Задачи MSBuild | Документация Майкрософт
description: Узнайте, как MSBuild использует задачи или блоки исполняемого кода, выполняющие атомарные операции сборки во время сборки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6b3bb4c1a17cd5d1481be2fa942686bce3861bb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918915"
---
# <a name="msbuild-tasks"></a>Задачи MSBuild

Платформе построения требуется возможность выполнения любого числа действий во время процесса построения. Для выполнения этих действий MSBuild использует *задачи*. Задача — это блок исполняемого кода, с помощью которого MSBuild выполняет атомарные операции построения.

## <a name="task-logic"></a>Алгоритмы задач

 Формат XML-файла проекта MSBuild не позволяет выполнять все операции, поэтому алгоритм задачи должен быть реализован за пределами файла проекта.

 Логика выполнения задачи реализована в виде класса платформы .NET, реализующего интерфейс <xref:Microsoft.Build.Framework.ITask>, который определен в пространстве имен <xref:Microsoft.Build.Framework>.

 Класс задач определяет также входные и выходные параметры, доступные задаче в файле проекта. Все открытые настраиваемые неабстрактные свойства, представляемые классом задач, получают значения в файле проекта путем помещения соответствующего атрибута с тем же именем в элемент [Задача](../msbuild/task-element-msbuild.md) и устанавливают его значение, как показано в примерах далее в этой статье.

 Для создания собственной задачи можно разработать управляемый класс, реализующий интерфейс <xref:Microsoft.Build.Framework.ITask>. Дополнительные сведения см. в статье [Написание задач](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Выполнение задачи из файла проекта

 Прежде чем выполнять задачу в файле проекта, необходимо сначала сопоставить тип в сборке, которая реализует задачу, с именем задачи с элементом [UsingTask](../msbuild/usingtask-element-msbuild.md). Это позволяет MSBuild знать, где искать алгоритм выполнения задачи при обнаружении ее в файле проекта.

 Чтобы выполнить задачу в файле проекта MSBuild, создайте элемент с именем таким же как у задачи в качестве дочернего элемента по отношению к элементу `Target`. Если задача принимает параметры, они передаются как атрибуты элемента.

 Списки элементов MSBuild и свойства можно использовать в качестве параметров. Например, следующий код вызывает задачу `MakeDir` и задает значение свойства `Directories` объекта `MakeDir` равным значению свойства `BuildDir`.

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

 MSBuild включает в себя много задач, например [Copy](../msbuild/copy-task.md) — копирование файлов, [MakeDir](../msbuild/makedir-task.md) — создание каталогов и [Csc](../msbuild/csc-task.md) — компиляция файлов исходного кода C#. Полный список доступных задач и сведения об их использовании см. в статье [Справочные сведения о задачах MSBuild](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Переопределенные задачи

 MSBuild ищет задачи в нескольких местах. Во первых, в файлах с расширением *.OverrideTasks*, которые хранятся в каталогах .NET Framework. Задачи в этих файлах переопределяют любые другие задачи с теми же именами, в том числе задачи в файле проекта. Второе место — файлы с расширением *.Tasks*, расположенные в каталогах .NET Framework. Если задача не найдена ни в одном из этих расположений, выполняется задача из файла проекта.

## <a name="see-also"></a>См. также

- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Написание задач](../msbuild/task-writing.md)
- [Встроенные задачи](../msbuild/msbuild-inline-tasks.md)
