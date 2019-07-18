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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0dd2ddfdbe784a45badfd0138b41b1f5dbff8ec7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954470"
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