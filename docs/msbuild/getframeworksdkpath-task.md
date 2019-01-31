---
title: Задача GetFrameworkSdkPath | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1ca2a4c77471f4b6767269e511d690c6c094a1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947274"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath - задача
Извлекает путь к [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
 В следующей таблице приводятся параметры задачи `GetFrameworkSdkPath` .  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 2.0 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 3.5 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Необязательный выходной параметр `String`, доступный только для чтения.<br /><br /> Возвращает путь к пакету SDK для .NET версии 4.0 при его наличии. В противном случае возвращает значение `String.Empty`.|  
|`Path`|Необязательный выходной параметр `String`.<br /><br /> Содержит путь к последнему пакету SDK для .NET при любой из его версий. В противном случае возвращает значение `String.Empty`.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `GetFrameworkSdkPath` для сохранения пути к [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] в свойстве `SdkPath`.  
  
```xml  
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