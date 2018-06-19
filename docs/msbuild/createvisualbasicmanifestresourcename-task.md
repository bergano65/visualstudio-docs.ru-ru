---
title: Задача CreateVisualBasicManifestResourceName | Документация Майкрософт
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
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20575936a6831e5001b2d3c0a413842969219c57
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572909"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>Задача CreateVisualBasicManifestResourceName
Создает имя манифеста в стиле [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] на основе заданного имени RESX-файла или другого ресурса.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры [задачи CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`ManifestResourceNames`|Выходной параметр <xref:Microsoft.Build.Framework.ITaskItem> `[]`, доступный только для чтения.<br /><br /> Итоговые имена манифестов.|  
|`ResourceFiles`|Обязательный параметр `String` .<br /><br /> Имя файла ресурсов, на основе которого создается имя манифеста [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`RootNamespace`|Необязательный параметр `String` .<br /><br /> Корневое пространство имен файла ресурсов, которое обычно берется из файла проекта. Может иметь значение `null`.|  
|`PrependCultureAsDirectory`|Необязательный параметр `Boolean` .<br /><br /> Если `true`, имя языка и региональных параметров добавляется в имя папки перед именем ресурса манифеста. Значение по умолчанию — `true`.|  
|`ResourceFilesWithManifestResourceNames`|Необязательный параметр вывода `String`, доступный только для чтения.<br /><br /> Возвращает имя файла ресурса, содержащее имя ресурса манифеста.|  
  
## <a name="remarks"></a>Примечания  
 [Задача CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) определяет имя соответствующего ресурса манифеста, которое будет назначено указанному RESX-файлу или другому файлу ресурсов. Задача присваивает логическое имя файлу ресурсов, а затем присоединяет его к параметру вывода в виде метаданных.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)