---
title: Задача Move | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8adfa75964959e2cce61779914a52f03319ed314
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592143"
---
# <a name="move-task"></a>Move - задача
Перемещает файлы в новое расположение.

## <a name="parameters"></a>Параметры
 В следующей таблице описаны параметры задачи `Move`.

|Параметр|Описание|
|---------------|-----------------|
|`DestinationFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает список файлов, в который будут перемещены исходные файлы. Предполагается, что этот список будет взаимно-однозначно сопоставляться со списком, указанным в параметре `SourceFiles`. Для перемещения первого файла из списка `SourceFiles` используется первый путь из списка `DestinationFiles` и т. д.|
|`DestinationFolder`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает каталог, в который вы хотите переместить файлы.|
|`MovedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит успешно перемещенные элементы.|
|`OverwriteReadOnlyFiles`|Необязательный параметр `Boolean`.<br /><br /> Значение `true` означает, что нужно перезаписывать даже файлы, доступные только для чтения.|
|`SourceFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы для перемещения.|

## <a name="remarks"></a>Примечания
 Можно указать либо параметр `DestinationFolder`, либо параметр `DestinationFiles`, но не оба одновременно. В противном случае задача прерывает работу и в журнале регистрируется ошибка.

 Задача `Move` создает все необходимые папки для указанного целевого расположения файлов.

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
