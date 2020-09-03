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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196578"
---
# <a name="cppclean-task"></a>Задача CPPClean
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Удаляет временные файлы, которые MSBuild создает при сборке проекта Visual C++. Процесс удаления файлов сборки называется *очисткой*.  

## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **CPPClean**.  

|            Параметр            |                                                                                                Description                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Необязательный выходной параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов выходного файла MSBuild, которые могут использоваться и создаваться задачами.                                |
|          **DoDelete**           |                                                            Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, выполняется очистка временных файлов сборки.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Обязательный параметр `String`.<br /><br /> Задает разделенный точками с запятой список расширений файлов для очистки.                                             |
|   **FilesExcludedFromClean**    |                                                    Необязательный параметр `String`.<br /><br /> Задает разделенный точками с запятой список файлов, очистка которых не производится.                                                    |
|       **FoldersToClean**        | Обязательный параметр `String`.<br /><br /> Задает разделенный точками с запятой список каталогов для очистки. Можно указать полный или относительный путь, а путь может содержать символ-шаблон ( **\\** \* ). |

## <a name="remarks"></a>Remarks  

## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
