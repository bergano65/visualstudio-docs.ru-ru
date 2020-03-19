---
title: Задача FindAppConfigFile | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54f3c222588cd13711c832d12f7598f0cc5e223
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634179"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile - задача

Выполняет поиск файла *app.config* (если он имеется) в предоставленных списках.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `FindAppConfigFile`.

|Параметр|Description|
|---------------|-----------------|
|`AppConfigFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает первый соответствующий элемент в списке (при его наличии).|
|`PrimaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает основной список для поиска.|
|`SecondaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает дополнительный список для поиска.|
|`TargetPath`|Обязательный параметр `String`.<br /><br /> Указывает значение для добавления в качестве метаданных.|

## <a name="remarks"></a>Remarks

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
