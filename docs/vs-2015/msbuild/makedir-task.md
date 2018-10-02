---
title: Задача MakeDir | Документы Майкрософт
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
- http://schemas.microsoft.com/developer/msbuild/2003#MakeDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MakeDir task [MSBuild]
- MSBuild, MakeDir task
ms.assetid: bc951577-1bfb-4100-b1f1-bc8278c45bf7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f5fe538d8e2c2976daa5d76d1aea73e0cbec7cd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570334"
---
# <a name="makedir-task"></a>Задача MakeDir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача MakeDir](https://docs.microsoft.com/visualstudio/msbuild/makedir-task).  
  
  
Создает каталоги и при необходимости любые родительские каталоги.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `MakeDir` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Directories`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Набор создаваемых каталогов.|  
|`DirectoriesCreated`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Каталоги, создаваемые этой задачей. Если не удается создать некоторые каталоги, этот параметр может содержать не все элементы, переданные в параметр `Directories`.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода использует задачу `MakeDir` для создания каталога, указанного свойством `OutputDirectory`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <OutputDirectory>\Output\</OutputDirectory>  
    </PropertyGroup>  
  
    <Target Name="CreateDirectories">  
        <MakeDir  
            Directories="$(OutputDirectory)"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



