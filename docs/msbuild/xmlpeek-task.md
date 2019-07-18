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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19b8273617955092519bf16f0aa5b3fbea86218a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62777825"
---
# <a name="xmlpeek-task"></a>XmlPeek - задача
Возвращает из XML-файла значения, указанные в запросе XPath.

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `XmlPeek` .

|Параметр|Описание|
|---------------|-----------------|
|`Namespaces`|Необязательный параметр `String` .<br /><br /> Задает пространства имен для префиксов запроса XPath.|
|`Query`|Необязательный параметр `String` .<br /><br /> Указывает запрос XPath.|
|`Result`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит результаты, возвращаемые этой задачей.|
|`XmlContent`|Необязательный параметр `String` .<br /><br /> Указывает входные данные XML в виде строки.|
|`XmlInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает входные данные XML в виде пути к файлу.|

## <a name="remarks"></a>Примечания
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)