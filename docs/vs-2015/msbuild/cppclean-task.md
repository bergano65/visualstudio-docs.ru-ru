---
title: Задача CPPClean | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 9437f72beef4f51568293543fcfaeeee2f65224c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562328"
---
# <a name="cppclean-task"></a>Задача CPPClean
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [cppclean-задача](https://docs.microsoft.com/visualstudio/msbuild/cppclean-task).  
  
  
Удаляет временные файлы, которые MSBuild создает при сборке проекта Visual C++. Процесс удаления файлов сборки называется *очисткой*.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **CPPClean**.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|**DeletedFiles**|Необязательный выходной параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов выходного файла MSBuild, которые могут использоваться и создаваться задачами.|  
|**DoDelete**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, выполняется очистка временных файлов сборки.|  
|**FilePatternsToDeleteOnClean**|Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список расширений файлов для очистки.|  
|**FilesExcludedFromClean**|Необязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список файлов, очистка которых не производится.|  
|**FoldersToClean**|Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список каталогов для очистки. Вы можете указать полный или относительный путь, который может содержать подстановочный знак (**\***).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



