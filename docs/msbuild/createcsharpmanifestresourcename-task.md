---
title: "Задача CreateCSharpManifestResourceName | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 574e04aa1c741c0a1720adf3fc77c2765f9dc1d3
ms.lasthandoff: 02/22/2017

---
# <a name="createcsharpmanifestresourcename-task"></a>Задача CreateCSharpManifestResourceName
Создает имя манифеста в стиле [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] на основе заданного имени RESX-файла или другого ресурса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры [задачи CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`ManifestResourceNames`|Необязательный параметр вывода, доступный только для чтения: <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Итоговые имена манифестов.|  
|`ResourceFiles`|Обязательный параметр `String`.<br /><br /> Имя файла ресурсов, на основе которого создается имя манифеста [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].|  
|`RootNamespace`|Необязательный параметр `String` .<br /><br /> Корневое пространство имен файла ресурсов, которое обычно берется из файла проекта. Может иметь значение `null`.|  
|`PrependCultureAsDirectory`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, имя языка и региональных параметров добавляется в имя папки перед именем ресурса манифеста. Значение по умолчанию — `true`.|  
|`ResourceFilesWithManifestResourceNames`|Необязательный параметр вывода `String`, доступный только для чтения.<br /><br /> Возвращает имя файла ресурса, содержащее имя ресурса манифеста.|  
  
## <a name="remarks"></a>Примечания  
 [Задача CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) определяет имя соответствующего ресурса манифеста, которое будет назначено указанному RESX-файлу или другому файлу ресурсов. Задача присваивает логическое имя файлу ресурсов, а затем присоединяет его к параметру вывода в виде метаданных.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует их от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
