---
title: "Задача GenerateTrustInfo | Документы Майкрософт"
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 9360cce21ab859e962734e240977c67627b8739f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="generatetrustinfo-task"></a>Задача GenerateTrustInfo
Создает доверие к приложению из базового манифеста и из параметров `TargetZone` и `ExcludedPermissions`.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `GenerateTrustInfo` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`ApplicationDependencies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает зависимые сборки.|  
|`BaseManifest`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает базовый манифест, на основе которого будет сформировано доверие к приложению.|  
|`ExcludedPermissions`|Необязательный параметр `String` .<br /><br /> Задает одно или несколько значений идентификаторов разрешений, разделенных точкой с запятой, которые должны быть исключены из набора разрешений зоны по умолчанию.|  
|`TargetZone`|Необязательный параметр `String` .<br /><br /> Определяет набор разрешений зоны по умолчанию, получаемый из политики компьютера.|  
|`TrustInfoFile`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает файл, содержащий сведения о безопасности доверия приложения.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)