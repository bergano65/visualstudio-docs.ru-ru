---
title: Задача XmlPeek | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e10cf26ad23e6fe4c881f68ad87bc80d04f2cf8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590973"
---
# <a name="xmlpeek-task"></a>XmlPeek - задача
Возвращает из XML-файла значения, указанные в запросе XPath.

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `XmlPeek` .

|Параметр|Описание|
|---------------|-----------------|
|`Namespaces`|Необязательный параметр `String`.<br /><br /> Задает пространства имен для префиксов запроса XPath.|
|`Query`|Необязательный параметр `String`.<br /><br /> Указывает запрос XPath.|
|`Result`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит результаты, возвращаемые этой задачей.|
|`XmlContent`|Необязательный параметр `String`.<br /><br /> Указывает входные данные XML в виде строки.|
|`XmlInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает входные данные XML в виде пути к файлу.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
