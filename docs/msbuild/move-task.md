---
title: "Задача Move | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 521a5239e47ffcab4d93c2cd2a46c30f881b0abd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="move-task"></a>Задача Move
Перемещает файлы в новое расположение.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи `Move`.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`DestinationFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает список файлов, в который будут перемещены исходные файлы. Предполагается, что этот список будет взаимно-однозначно сопоставляться со списком, указанным в параметре `SourceFiles`. Для перемещения первого файла из списка `SourceFiles` используется первый путь из списка `DestinationFiles` и т. д.|  
|`DestinationFolder`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает каталог, в который вы хотите переместить файлы.|  
|`MovedFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит успешно перемещенные элементы.|  
|`OverwriteReadOnlyFiles`|Необязательный параметр `Boolean` .<br /><br /> Значение `true` означает, что нужно перезаписывать даже файлы, доступные только для чтения.|  
|`SourceFiles`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает файлы для перемещения.|  
  
## <a name="remarks"></a>Примечания  
 Можно указать либо параметр `DestinationFolder`, либо параметр `DestinationFiles`, но не оба одновременно. В противном случае задача прерывает работу и в журнале регистрируется ошибка.  

 Задача `Move` создает все необходимые папки для указанного целевого расположения файлов.

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
