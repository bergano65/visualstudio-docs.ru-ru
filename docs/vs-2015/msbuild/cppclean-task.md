---
title: Задача CPPClean | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bddba1170cf675b5bde7ab8deed8cce1e7eb57dd
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655001"
---
# <a name="cppclean-task"></a>Задача CPPClean
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Удаляет временные файлы, которые MSBuild создает при сборке проекта Visual C++. Процесс удаления файлов сборки называется *очисткой*.  

## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **CPPClean**.  

|            Параметр            |                                                                                                Описание                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Необязательный выходной параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов выходного файла MSBuild, которые могут использоваться и создаваться задачами.                                |
|          **DoDelete**           |                                                            Необязательный параметр **Boolean** .<br /><br /> Если задано значение `true`, выполняется очистка временных файлов сборки.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список расширений файлов для очистки.                                             |
|   **FilesExcludedFromClean**    |                                                    Необязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список файлов, очистка которых не производится.                                                    |
|       **FoldersToClean**        | Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список каталогов для очистки. Вы можете указать полный или относительный путь, который может содержать подстановочный знак (**\\**\*). |

## <a name="remarks"></a>Примечания  

## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
