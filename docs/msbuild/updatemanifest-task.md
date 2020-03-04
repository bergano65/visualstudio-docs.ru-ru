---
title: Задача UpdateManifest | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e410ba3122e0065f92186195ee5a82d6a55c2f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631346"
---
# <a name="updatemanifest-task"></a>UpdateManifest - задача

Обновляет выбранные свойства в манифесте и выполняет повторное подписание.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `UpdateManifest` .

|Параметр|Описание|
|---------------|-----------------|
|`ApplicationManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест приложения.|
|`ApplicationPath`|Обязательный параметр `String` .<br /><br /> Указывает путь к манифесту приложения.|
|`InputManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест, подлежащий обновлению.|
|`OutputManifest`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, содержащий обновленные свойства.|

## <a name="remarks"></a>Примечания

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в статье [Базовый класс Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)