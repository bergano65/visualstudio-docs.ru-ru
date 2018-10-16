---
title: Задача CreateCSharpManifestResourceName | Документация Майкрософт
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
- MSBuild, CreateCSharpManifestResourceName task
- CreateCSharpManifestResourceName task [MSBuild]
ms.assetid: 2ace88c1-d757-40a7-8158-c1d3f5ff0511
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32aa7fdb5779d7ae042e8efa9652f25df70a2754
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247849"
---
# <a name="createcsharpmanifestresourcename-task"></a>Задача CreateCSharpManifestResourceName
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Создает имя манифеста в стиле [!INCLUDE[csprcs](../includes/csprcs-md.md)] на основе заданного имени RESX-файла или другого ресурса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры [задачи CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md).  
  
|Параметр|Описание|  
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



