---
title: "Задача UpdateManifest | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 609f057cd5284ff88d6b73870850a678e500ee14
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="updatemanifest-task"></a>Задача UpdateManifest
Обновляет выбранные свойства в манифесте и выполняет повторное подписание.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `UpdateManifest` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`ApplicationManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест приложения.|  
|`ApplicationPath`|Обязательный параметр `String` .<br /><br /> Указывает путь к манифесту приложения.|  
|`InputManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест, подлежащий обновлению.|  
|`OutputManifest`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, содержащий обновленные свойства.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Task Base Class](../msbuild/task-base-class.md) (Базовый класс Task).  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)