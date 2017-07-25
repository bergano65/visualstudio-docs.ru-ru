---
title: "Задача RegisterAssembly | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: e1e6b68c59aa10204bd985b9bf8d17e8256936d5
ms.contentlocale: ru-ru
ms.lasthandoff: 05/30/2017

---
# <a name="registerassembly-task"></a>Задача RegisterAssembly
Cчитывает метаданные указанной сборки и добавляет в реестр необходимые записи, что позволяет COM-клиентам прозрачно создавать классы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Поведение этой задачи близко к поведению [средства регистрации сборок Regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), но не идентично ему.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `RegisterAssembly`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Assemblies`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает сборки для регистрации в COM.|  
|`AssemblyListFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Содержит сведения о состоянии взаимодействия между задачей `RegisterAssembly` и задачей [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Это препятствует попытке задачи `UnregisterAssembly` отменить регистрацию сборки, которая не смогла зарегистрироваться в задаче `RegisterAssembly`.|  
|`CreateCodeBase`|Необязательный параметр `Boolean` .<br /><br /> Если он имеет значение `true`, то в реестре создается запись codebase, которая указывает путь к файлу сборки, не установленному в глобальном кэше сборок. Не следует указывать этот параметр, если впоследствии вы будете устанавливать регистрируемую сборку в глобальном кэше сборок.|  
|`TypeLibFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает библиотеку типов, которую нужно создать из указанной сборки. Создаваемая библиотека типов содержит определения типов, заданные в сборке. Библиотека типов создается только в том случае, если выполняется одно из следующих условий:<br /><br /> — библиотеки типов с таким именем не существует в этом расположении;<br />— библиотека типов существует, но она старше передаваемой сборки.<br /><br /> Если библиотека типов новее, чем передаваемая сборка, то новая библиотека не создается, но сборка будет зарегистрирована.<br /><br /> Если указан этот параметр, он должен иметь такое же количество элементов, как и параметр `Assemblies`, иначе задача завершится сбоем. Если не указаны входные данные, задача по умолчанию использует имя сборки, добавляя к нему расширение .tlb.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере задача `RegisterAssembly` регистрирует сборки, определенные в коллекции элементов `MyAssemblies`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
