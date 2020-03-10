---
title: Задача CreateCSharpManifestResourceName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8e72ef282911ecb36fb9a16838f6cc311e253e1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634361"
---
# <a name="createcsharpmanifestresourcename-task"></a>CreateCSharpManifestResourceName - задача

Создает имя манифеста в стиле C# на основе заданного имени *RESX*-файла или другого ресурса.

## <a name="parameters"></a>Параметры

 В следующей таблице описаны параметры [задачи CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).

| Параметр | Описание |
| - | - |
| `ManifestResourceNames` | Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`, доступный только для чтения.<br /><br /> Итоговые имена манифестов. |
| `ResourceFiles` | Обязательный параметр `String` .<br /><br /> Имя файла ресурсов, из которого следует создать имя манифеста C#. |
| `RootNamespace` | Необязательный параметр `String`.<br /><br /> Корневое пространство имен файла ресурсов, которое обычно берется из файла проекта. Может иметь значение `null`. |
| `PrependCultureAsDirectory` | Необязательный параметр `Boolean`.<br /><br /> Если `true`, имя языка и региональных параметров добавляется в имя папки перед именем ресурса манифеста. Значение по умолчанию — `true`. |
| `ResourceFilesWithManifestResourceNames` | Необязательный параметр вывода `String`, доступный только для чтения.<br /><br /> Возвращает имя файла ресурса, содержащее имя ресурса манифеста. |

## <a name="remarks"></a>Примечания

 [Задача CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) определяет имя соответствующего ресурса манифеста, которое будет назначено указанному *RESX*-файлу или другому файлу ресурсов. Задача присваивает логическое имя файлу ресурсов, а затем присоединяет его к параметру вывода в виде метаданных.

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
