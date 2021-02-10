---
title: Задача CreateVisualBasicManifestResourceName | Документация Майкрософт
description: Используйте задачу CreateVisualBasicManifestResourceName MSBuild, чтобы создать имя манифеста в стиле Visual Basic на основе указанного имени RESX-файла или другого ресурса.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8e9f0868cb774ee82c79ba190acddebf63193cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901381"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>CreateVisualBasicManifestResourceName - задача

Создает имя манифеста в стиле Visual Basic на основе заданного имени *RESX*-файла или другого ресурса.

## <a name="parameters"></a>Параметры

 В следующей таблице описаны параметры [задачи CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Параметр | Описание |
| - | - |
| `ManifestResourceNames` | Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`, доступный только для чтения.<br /><br /> Итоговые имена манифестов. |
| `ResourceFiles` | Обязательный параметр `String`.<br /><br /> Имя файла ресурсов, из которого следует создать имя манифеста Visual Basic. |
| `RootNamespace` | Необязательный параметр `String`.<br /><br /> Корневое пространство имен файла ресурсов, которое обычно берется из файла проекта. Может иметь значение `null`. |
| `PrependCultureAsDirectory` | Необязательный параметр `Boolean`.<br /><br /> Если `true`, имя языка и региональных параметров добавляется в имя папки перед именем ресурса манифеста. Значение по умолчанию — `true`. |
| `ResourceFilesWithManifestResourceNames` | Необязательный параметр вывода `String`, доступный только для чтения.<br /><br /> Возвращает имя файла ресурса, содержащее имя ресурса манифеста. |

## <a name="remarks"></a>Remarks

 [Задача CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) определяет имя соответствующего ресурса манифеста, которое будет назначено указанному *RESX*-файлу или другому файлу ресурсов. Задача присваивает логическое имя файлу ресурсов, а затем присоединяет его к параметру вывода в виде метаданных.

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
