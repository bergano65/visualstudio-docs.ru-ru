---
title: Задача CPPClean | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a871effd2b7560cc34ae8e2a91c0b55f63bcfe44
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="cppclean-task"></a>Задача CPPClean
Удаляет временные файлы, которые MSBuild создает при сборке проекта Visual C++. Процесс удаления файлов сборки называется *очисткой*.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **CPPClean**.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|**DeletedFiles**|Необязательный выходной параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов выходного файла MSBuild, которые могут использоваться и создаваться задачами.|  
|**DoDelete**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, выполняется очистка временных файлов сборки.|  
|**FilePatternsToDeleteOnClean**|Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список расширений файлов для очистки.|  
|**FilesExcludedFromClean**|Необязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список файлов, очистка которых не производится.|  
|**FoldersToClean**|Обязательный параметр `String` .<br /><br /> Задает разделенный точками с запятой список каталогов для очистки. Вы можете указать полный или относительный путь, который может содержать подстановочный знак (**\***).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)