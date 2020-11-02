---
title: Задача CPPClean | Документы Майкрософт
description: В этой статье описывается задача CPPClean, которая используется для удаления временных файлов, создаваемых MSBuild при сборке проекта на C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8f59b66ab1fc117a29d7ed8db2d380b4b11b437
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796112"
---
# <a name="cppclean-task"></a>Задача CPPClean

Удаляет временные файлы, которые MSBuild создает при сборке проекта C++. Процесс удаления файлов сборки называется *очисткой* .

## <a name="parameters"></a>Параметры

 В следующей таблице описаны параметры задачи **CPPClean** .

|Параметр|Описание|
|---------------|-----------------|
|**DeletedFiles**|Необязательный выходной параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов выходного файла MSBuild, которые могут использоваться и создаваться задачами.|
|**DoDelete**|Необязательный параметр **Boolean** .<br /><br /> Если задано значение `true`, выполняется очистка временных файлов сборки.|
|**FilePatternsToDeleteOnClean**|Обязательный параметр `String`.<br /><br /> Задает разделенный точками с запятой список расширений файлов для очистки.|
|**FilesExcludedFromClean**|Необязательный параметр `String`.<br /><br /> Задает разделенный точками с запятой список файлов, очистка которых не производится.|
|**FoldersToClean**|Обязательный параметр `String`.<br /><br /> Задает разделенный точками с запятой список каталогов для очистки. Вы можете указать полный или относительный путь, который может содержать подстановочный знак (*).|

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
