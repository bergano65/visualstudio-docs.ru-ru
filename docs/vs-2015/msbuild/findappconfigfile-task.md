---
title: Задача FindAppConfigFile | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb9e1f3fbdc1a6f4d7c4e2c589f620f331a904ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179607"
---
# <a name="findappconfigfile-task"></a>Задача FindAppConfigFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Выполняет поиск файла app.config (если он имеется) в предоставленных списках.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FindAppConfigFile`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`AppConfigFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает первый соответствующий элемент в списке (при его наличии).|  
|`PrimaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает основной список для поиска.|  
|`SecondaryList`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает дополнительный список для поиска.|  
|`TargetPath`|Обязательный параметр `String`.<br /><br /> Указывает значение для добавления в качестве метаданных.|  
  
## <a name="remarks"></a>Remarks  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
