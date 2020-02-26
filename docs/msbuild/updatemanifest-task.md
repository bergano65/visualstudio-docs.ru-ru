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
ms.openlocfilehash: 215092d7fbcee8ec30210dd8332bc6ae5b7ad412
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578280"
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