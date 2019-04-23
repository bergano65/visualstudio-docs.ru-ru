---
title: Задача Move | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab75ccebd618946454c3386f564e3f6199409935
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657120"
---
# <a name="move-task"></a>Задача Move
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
