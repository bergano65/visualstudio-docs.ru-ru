---
title: Задача AssignProjectConfiguration | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d771117829ab8ef37ea495b4862ffa492e686770
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31567620"
---
# <a name="assignprojectconfiguration-task"></a>Задача AssignProjectConfiguration
Эта задача принимает строки конфигурации списка и назначает их конкретным проектам.  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `AssignProjectConfiguration`.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Необязательный выходной параметр `string`.<br /><br /> Содержит строку XML с конфигурацией для каждого проекта. Конфигурации назначаются именованным проектам.|  
|`DefaultToVcxPlatformMapping`|Необязательный выходной параметр `string`.<br /><br /> Содержит разделенный точками с запятой список сопоставлений от имен платформы,<br /><br /> используемых большинством типов, до имен, используемых VCXPROJ-файлами.<br /><br /> Пример:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> Выходной параметр `string`.<br /><br /> Содержит разделенный точками с запятой список сопоставлений от имен платформы VCXPROJ до имен, используемых большинством типов.<br /><br /> Пример:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Необязательный выходной параметр `string`.<br /><br /> Содержит конфигурацию для текущего проекта.|  
|`CurrentProjectPlatform`|Необязательный выходной параметр `string`.<br /><br /> Содержит платформу для текущего проекта.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Необязательный выходной параметр `bool`.<br /><br /> Содержит флаг, показывающий, нужно ли создавать ссылки несмотря на то, что они были отключены в конфигурации проекта.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Необязательный выходной параметр `bool`.<br /><br /> Содержит флаг, указывающий, нужно ли не задавать родительскую конфигурацию и платформу.|  
|`OutputType`|Необязательный выходной параметр `string`.<br /><br /> Содержит тип выходных данных для проекта.|  
|`ResolveConfigurationPlatformUsingMappings`|Необязательный выходной параметр `bool`.<br /><br /> Содержит флаг, показывающий, должна ли сборка использовать сопоставления по умолчанию для разрешения конфигурации и платформы в переданных ссылках проекта.|  
|`AssignedProjects`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список разрешенных путей ссылок.|  
|`UnassignedProjects`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит список элементов ссылок проекта, которые не удалось разрешить с помощью предварительно разрешенного списка выходных файлов.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)