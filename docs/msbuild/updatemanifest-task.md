---
title: Задача UpdateManifest | Документация Майкрософт
description: Сведения об использовании задачи UpdateManifest в MSBuild для обновления выбранных свойств в манифесте и повторного подписания.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4fab3844b21e12edceb83da310e9069199578ef6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046859"
---
# <a name="updatemanifest-task"></a>UpdateManifest - задача

Обновляет выбранные свойства в манифесте и выполняет повторное подписание.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `UpdateManifest` .

|Параметр|Описание|
|---------------|-----------------|
|`ApplicationManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест приложения.|
|`ApplicationPath`|Обязательный параметр `String`.<br /><br /> Указывает путь к манифесту приложения.|
|`InputManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, подлежащий обновлению.|
|`OutputManifest`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, содержащий обновленные свойства.|

## <a name="remarks"></a>Комментарии

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в статье [Базовый класс Task](../msbuild/task-base-class.md).

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)