---
title: Задача FindInList | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4a9d6a1fc6dbf8f160400ffae10a4a5fb355f3d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206808"
---
# <a name="findinlist-task"></a>Задача FindInList
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Выполняет поиск элемента с указанной спецификацией в заданном списке.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры [задачи FindInList](../msbuild/findinlist-task.md).  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`CaseSensitive`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, при поиске учитывается регистр, в противном случае регистр не учитывается. Значение по умолчанию — `true`.|  
|`FindLastMatch`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, возвращается последнее совпадение, в противном случае возвращается первое совпадение. Значение по умолчанию — `false`.|  
|`ItemFound`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` , доступный только для чтения.<br /><br /> Первый соответствующий элемент в списке (при его наличии).|  
|`ItemSpecToFind`|Обязательный параметр `String` .<br /><br /> Спецификация элементов, которую требуется найти.|  
|`List`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Список, в котором нужно найти спецификацию элементов.|  
|`MatchFileNameOnly`|Необязательный параметр `Boolean` .<br /><br /> Если задано значение `true`, сравнение проводится только по той части спецификации элементов, которая относится к имени файла, в противном случае — по всей спецификации. Значение по умолчанию — `true`.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



