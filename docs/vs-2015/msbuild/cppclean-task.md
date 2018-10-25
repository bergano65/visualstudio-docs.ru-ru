---
title: Задача CPPClean | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: a96571cbc4de4281daddd42f4b1d53b60b300e53
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826951"
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
|       **FoldersToClean**        | Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список каталогов для очистки. Можно указать полный или относительный путь, а путь может содержать подстановочный знак (**\\**\*). |

## <a name="remarks"></a>Примечания  

## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



