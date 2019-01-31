---
title: Задача UpdateManifest | Документация Майкрософт
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
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54364f40c25deb4a32431c42f74d76bbdd42b155
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802151"
---
# <a name="updatemanifest-task"></a>Задача UpdateManifest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Обновляет выбранные свойства в манифесте и выполняет повторное подписание.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `UpdateManifest` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`ApplicationManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест приложения.|  
|`ApplicationPath`|Обязательный параметр `String` .<br /><br /> Указывает путь к манифесту приложения.|  
|`InputManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Указывает манифест, подлежащий обновлению.|  
|`OutputManifest`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, содержащий обновленные свойства.|  
  
## <a name="remarks"></a>Примечания  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Task Base Class](../msbuild/task-base-class.md) (Базовый класс Task).  
  
## <a name="see-also"></a>См. также раздел  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
