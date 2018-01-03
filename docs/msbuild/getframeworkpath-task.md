---
title: "Задача GetFrameworkPath | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ba676aa3aeef0cffb5b6de6b086c7a75c5ffb458
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="getframeworkpath-task"></a>Задача GetFrameworkPath
Извлекает путь к сборкам [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `GetFrameworkPath`.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к сборкам платформы .NET Framework версии 1.1, если они есть. В противном случае возвращает значение `null`.|  
|`FrameworkVersion20Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к сборкам платформы .NET Framework версии 2.0, если они есть. В противном случае возвращает значение `null`.|  
|`FrameworkVersion30Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к сборкам платформы .NET Framework версии 3.0, если они есть. В противном случае возвращает значение `null`.|  
|`FrameworkVersion35Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к сборкам платформы .NET Framework версии 3.5, если они есть. В противном случае возвращает значение `null`.|  
|`FrameworkVersion40Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к сборкам платформы .NET Framework версии 4.0, если они есть. В противном случае возвращает значение `null`.|  
|`Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к самым новым сборкам платформы, если они есть. В противном случае возвращает значение `null`.|  
  
## <a name="remarks"></a>Примечания  
 Если установлено несколько версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], эта задача возвращает версию, для которой предназначен [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `GetFrameworkPath` для сохранения пути к [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] в свойстве `FrameworkPath`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)