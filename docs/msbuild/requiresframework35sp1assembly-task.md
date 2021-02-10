---
title: Задача RequiresFramework35SP1Assembly | Документы Майкрософт
description: Узнайте, как с помощью задачи RequiresFramework35SP1Assembly в MSBuild определить, что приложению требуется .NET Framework 3.5 с пакетом обновления 1 (SP1).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04b435df9b028689ea6c0d1f2c61e7e8df8bb8bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931764"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly - задача

Определяет, требуется ли для приложения платформа .NET Framework 3.5 SP1.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `RequiresFramework35SP1Assembly` .

|Параметр|Description|
|---------------|-----------------|
|`Assemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, на которые в приложении есть ссылки.|
|`CreateDesktopShortcut`|Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, создает значок ярлыка на рабочем столе во время установки.|
|`DeploymentManifestEntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает имя файла манифеста для приложения.|
|`EntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает сборку, которую следует выполнить при запуске приложения.|
|`ErrorReportUrl`|Необязательный параметр `String`.<br /><br /> Указывает веб-сайт, который отображается в диалоговых окнах во время установок ClickOnce.|
|`Files`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает список файлов, которые будут развернуты при публикации приложения.|
|`ReferencedAssemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, на которые в проекте есть ссылки.|
|`RequiresMinimumFramework35SP1`|Необязательный выходной параметр `Boolean`.<br /><br /> Если задано значение `true`, для приложения требуется платформа .NET Framework 3.5 с пакетом обновления 1 (SP1).|
|`SigningManifests`|Необязательный выходной параметр `Boolean`.<br /><br /> Если задано значение `true`, манифесты ClickOnce подписаны.|
|`SuiteName`|Необязательный параметр `String`.<br /><br /> Задает имя папки в меню **Пуск**, куда будет установлено приложение.|
|`TargetFrameworkVersion`|Необязательный параметр `String`.<br /><br /> Задает версию платформы .NET Framework, для которой предназначено приложение.|

## <a name="remarks"></a>Remarks

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)