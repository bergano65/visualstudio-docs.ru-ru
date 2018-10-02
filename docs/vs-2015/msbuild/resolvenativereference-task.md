---
title: Задача ResolveNativeReference | Документация Майкрософт
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
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06171281706b2395cbac0c98b5b8a76c4da363c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558833"
---
# <a name="resolvenativereference-task"></a>Задача ResolveNativeReference
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача ResolveNativeReference](https://docs.microsoft.com/visualstudio/msbuild/resolvenativereference-task).  
  
  
Разрешает машинные ссылки. Реализует класс <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Этот класс поддерживает инфраструктуру .NET Framework, которая не предназначена для использования непосредственно из программного кода.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `ResolveNativeReference`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|Требуется [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)`[]` параметра.<br /><br /> Получает или задает пути поиска для разрешения идентификаторов сборок для собственных ссылок.|  
|`ContainedComComponents`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает компоненты COM машинной сборки.|  
|`ContainedLooseEtcFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Возвращает или задает свободные ETC-файлы, перечисленные в собственном манифесте.|  
|`ContainedLooseTlbFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает свободные TLB-файлы машинной сборки.|  
|`ContainedPrerequisiteAssemblies`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает сборки, которые должны быть созданы до использования манифеста.|  
|`ContainedTypeLibraries`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает библиотеки типов машинной сборки.|  
|`ContainingReferenceFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Получает или задает файлы ссылок.|  
|`NativeReferences`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Получает или задает ссылки на сборки в машинном коде Win32.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



