---
title: Задача ResolveNonMSBuildProjectOutput | Документы Майкрософт
description: Сведения об использовании задачи ResolveNonMSBuildProjectOutput в MSBuild для определения выходных файлов для ссылок на проекты, не относящиеся к MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98d8e483b8ad03f02283620f65ec0351d9d64051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912464"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput - задача

Определяет выходные файлы для ссылок на проекты, не относящихся к MSBuild.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `ResolveNonMSBuildProjectOutput` .

|Параметр|Описание|
|---------------|-----------------|
|`PreresolvedProjectOutputs`|Необязательный параметр `String`.<br /><br /> Задает XML-строку, содержащую разрешенные выходные данные проекта.|
|`ProjectReferences`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает ссылки проекта.|
|`ResolvedOutputPaths`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список путей разрешенных ссылок (и сохраняет исходные атрибуты ссылок проекта).|
|`UnresolvedProjectReferences`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список элементов ссылок проекта, которые не удалось разрешить с помощью предварительно разрешенного списка выходных данных.<br /><br /> Так как Visual Studio предварительно разрешает только проекты, отличные от MSBuild, ссылки проекта в этом списке имеют формат MSBuild.|

## <a name="remarks"></a>Remarks

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)