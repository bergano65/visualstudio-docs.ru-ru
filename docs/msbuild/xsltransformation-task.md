---
title: Задача XslTransformation | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84bc83f60d133dcaf22c9fa690357fa2624adabd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630799"
---
# <a name="xsltransformation-task"></a>XslTransformation - задача

Преобразует входные данные XML с помощью XSLT или скомпилированного XSLT и выводит результат на устройство вывода или в выходной файл.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `XslTransformation` .

|Параметр|Описание|
|---------------|-----------------|
|`OutputPaths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает выходные файлы для преобразования XML.|
|`Parameters`|Необязательный параметр `String`.<br /><br /> Задает параметры для входного документа XSLT.|
|`XmlContent`|Необязательный параметр `String`.<br /><br /> Указывает входные данные XML в виде строки.|
|`XmlInputPaths`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает входные файлы XML.|
|`XslCompiledDllPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает скомпилированный XSLT.|
|`XslContent`|Необязательный параметр `String`.<br /><br /> Указывает входные данные XSLT в виде строки.|
|`XslInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает входной файл XSLT.|

## <a name="remarks"></a>Примечания

 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
