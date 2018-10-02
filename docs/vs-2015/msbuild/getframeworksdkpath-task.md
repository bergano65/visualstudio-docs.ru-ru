---
title: Задача GetFrameworkSdkPath | Документы Майкрософт
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
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3e35cac8399ab97ae3825e35de5b249db7e23a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557896"
---
# <a name="getframeworksdkpath-task"></a>Задача GetFrameworkSdkPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [задача GetFrameworkSdkPath](https://docs.microsoft.com/visualstudio/msbuild/getframeworksdkpath-task).  
  
  
Извлекает путь к [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `GetFrameworkSdkPath`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 2.0 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 3.5 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 4.0 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к последнему пакету SDK для .NET при любой из его версий. В противном случае возвращает значение `String.Empty`.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `GetFrameworkSdkPath` для сохранения пути к [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] в свойстве `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)



