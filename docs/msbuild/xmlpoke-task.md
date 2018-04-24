---
title: Задача XmlPoke | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05bef838c905b12ba76d22bec901ae4eb3382c5f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="xmlpoke-task"></a>Задача XmlPoke
Задает в XML-файле значения, указанные в запросе XPath.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `XmlPoke` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Namespaces`|Необязательный параметр `String` .<br /><br /> Задает пространства имен для префиксов запроса XPath.|  
|`Query`|Необязательный параметр `String` .<br /><br /> Указывает запрос XPath.|  
|`Value`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Задает выходной файл.|  
|`XmlInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает входные данные XML в виде пути к файлу.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)