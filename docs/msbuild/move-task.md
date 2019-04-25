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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc2e11a1466f359cebb60505f498c0df3ae6c45b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817526"
---
# <a name="move-task"></a>Move - задача
Перемещает файлы в новое расположение.

## <a name="parameters"></a>Параметры
 В следующей таблице описаны параметры задачи `Move`.

|Параметр|Описание|
|---------------|-----------------|
|`DestinationFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает список файлов, в который будут перемещены исходные файлы. Предполагается, что этот список будет взаимно-однозначно сопоставляться со списком, указанным в параметре `SourceFiles`. Для перемещения первого файла из списка `SourceFiles` используется первый путь из списка `DestinationFiles` и т. д.|
|`DestinationFolder`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает каталог, в который вы хотите переместить файлы.|
|`MovedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит успешно перемещенные элементы.|
|`OverwriteReadOnlyFiles`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` означает, что нужно перезаписывать даже файлы, доступные только для чтения.|
|`SourceFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы для перемещения.|

## <a name="remarks"></a>Примечания
 Можно указать либо параметр `DestinationFolder`, либо параметр `DestinationFiles`, но не оба одновременно. В противном случае задача прерывает работу и в журнале регистрируется ошибка.

 Задача `Move` создает все необходимые папки для указанного целевого расположения файлов.

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
