---
title: "Задача XmlPeek | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7238e549011d5f80ce2c8f006f56f6bb0f2de58d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="xmlpeek-task"></a>Задача XmlPeek
Возвращает из XML-файла значения, указанные в запросе XPath.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `XmlPeek` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Namespaces`|Необязательный параметр `String` .<br /><br /> Задает пространства имен для префиксов запроса XPath.|  
|`Query`|Необязательный параметр `String` .<br /><br /> Указывает запрос XPath.|  
|`Result`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит результаты, возвращаемые этой задачей.|  
|`XmlContent`|Необязательный параметр `String` .<br /><br /> Указывает входные данные XML в виде строки.|  
|`XmlInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает входные данные XML в виде пути к файлу.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)