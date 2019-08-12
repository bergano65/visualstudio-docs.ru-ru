---
title: Задача UnregisterAssembly | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ef7ef7f4ec930b8aa338a8be33c4009b3009b20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193234"
---
# <a name="unregisterassembly-task"></a>Задача UnregisterAssembly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отменяет регистрацию указанных сборок для целей COM-взаимодействия. Эта задача противоположна [задаче RegisterAssembly](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `UnregisterAssembly` .  
  
|Параметр|ОПИСАНИЕ|  
|---------------|-----------------|  
|`Assemblies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает сборки, регистрацию которых следует отменить.|  
|`AssemblyListFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Содержит сведения о состоянии взаимодействия между задачами `RegisterAssembly` и `UnregisterAssembly`. Благодаря этому задача не пытается отменить регистрацию для сборки, которую не удалось зарегистрировать в задаче `RegisterAssembly`.<br /><br /> Если этот параметр указан, параметры `Assemblies` и `TypeLibFiles` игнорируются.|  
|`TypeLibFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Отменяет регистрацию библиотеки заданного типа в указанной сборке. **Примечание.** Этот параметр является обязательным только в том случае, если имя файла библиотеки типов отличается от имени сборки.|  
  
## <a name="remarks"></a>Примечания  
 Для успешного выполнения задачи не требуется, чтобы существовала указанная сборка. Если вы попытаетесь отменить регистрацию несуществующей сборки, задача завершится успешно с предупреждением. Такая логика объясняется тем, что целью этой задачи является удаление регистрации сборки из реестра. Если сборка не существует, то в реестре нет информации о ней, следовательно, задача выполнена успешно.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, который, в свою очередь, наследует от класса <xref:System.MarshalByRefObject>. Класс `MarshalByRefObject` предоставляет те же возможности, что и класс <xref:Microsoft.Build.Utilities.Task>, но его экземпляр можно создать в собственном домене приложения.  
  
## <a name="example"></a>Пример  
 В следующем примере задача `UnregisterAssembly` отменяет регистрацию сборки, расположенной по пути, указанному в свойствах `OutputPath` и `FileName`, если такая сборка существует.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [RegisterAssembly Task](../msbuild/registerassembly-task.md)  (Задача RegisterAssembly)  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
