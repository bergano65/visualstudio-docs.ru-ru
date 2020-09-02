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
ms.openlocfilehash: 5e2ec8a0cd854a04c338add22c3f90daf0bf14ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159205"
---
# <a name="updatemanifest-task"></a>Задача UpdateManifest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обновляет выбранные свойства в манифесте и выполняет повторное подписание.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `UpdateManifest`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`ApplicationManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест приложения.|  
|`ApplicationPath`|Обязательный параметр `String`.<br /><br /> Указывает путь к манифесту приложения.|  
|`InputManifest`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, подлежащий обновлению.|  
|`OutputManifest`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает манифест, содержащий обновленные свойства.|  
  
## <a name="remarks"></a>Remarks  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс Task](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
