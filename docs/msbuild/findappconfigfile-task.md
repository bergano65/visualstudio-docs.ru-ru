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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0033bcb21922d6f7e0204b1555fa2c46f8d91d50
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597560"
---
# <a name="findappconfigfile-task"></a>FindAppConfigFile - задача
Выполняет поиск файла *app.config* (если он имеется) в предоставленных списках.

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `FindAppConfigFile` .

|Параметр|Описание|
|---------------|-----------------|
|`AppConfigFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает первый соответствующий элемент в списке (при его наличии).|
|`PrimaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает основной список для поиска.|
|`SecondaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает дополнительный список для поиска.|
|`TargetPath`|Обязательный параметр `String` .<br /><br /> Указывает значение для добавления в качестве метаданных.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)