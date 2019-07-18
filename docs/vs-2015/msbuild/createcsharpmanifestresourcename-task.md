---
title: Задача CreateCSharpManifestResourceName | Документация Майкрософт
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9308f94e865bfe54384719d8f57f3ad1819c79fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184047"
---
# <a name="createcsharpmanifestresourcename-task"></a>Задача CreateCSharpManifestResourceName
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создает имя манифеста в стиле [!INCLUDE[csprcs](../includes/csprcs-md.md)] на основе заданного имени RESX-файла или другого ресурса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры [задачи CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`ManifestResourceNames`|Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`, доступный только для чтения.<br /><br /> Итоговые имена манифестов.|  
|`ResourceFiles`|Обязательный параметр `String` .<br /><br /> Имя файла ресурсов, на основе которого создается имя манифеста [!INCLUDE[csprcs](../includes/csprcs-md.md)].|  
|`RootNamespace`|Необязательный параметр `String` .<br /><br /> Корневое пространство имен файла ресурсов, которое обычно берется из файла проекта. Может иметь значение `null`.|  
|`PrependCultureAsDirectory`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, имя языка и региональных параметров добавляется в имя папки перед именем ресурса манифеста. Значение по умолчанию — `true`.|  
|`ResourceFilesWithManifestResourceNames`|Необязательный параметр вывода `String`, доступный только для чтения.<br /><br /> Возвращает имя файла ресурса, содержащее имя ресурса манифеста.|  
  
## <a name="remarks"></a>Примечания  
 [Задача CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) определяет имя соответствующего ресурса манифеста, которое будет назначено указанному RESX-файлу или другому файлу ресурсов. Задача присваивает логическое имя файлу ресурсов, а затем присоединяет его к параметру вывода в виде метаданных.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
