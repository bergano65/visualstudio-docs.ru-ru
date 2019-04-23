---
title: Задача XslTransformation | Документация Майкрософт
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
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1705fd2b79f8b5044aa4ffa0b65801d6db6c7f33
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665562"
---
# <a name="xsltransformation-task"></a>Задача XslTransformation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Преобразует входные данные XML с помощью XSLT или скомпилированного XSLT и выводит результат на устройство вывода или в выходной файл.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `XslTransformation` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`OutputPaths`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Задает выходные файлы для преобразования XML.|  
|`Parameters`|Необязательный параметр `String` .<br /><br /> Задает параметры для входного документа XSLT.|  
|`XmlContent`|Необязательный параметр `String` .<br /><br /> Указывает входные данные XML в виде строки.|  
|`XmlInputPaths`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает входные файлы XML.|  
|`XslCompiledDllPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Задает скомпилированный XSLT.|  
|`XslContent`|Необязательный параметр `String` .<br /><br /> Указывает входные данные XSLT в виде строки.|  
|`XslInputPath`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает входной файл XSLT.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
