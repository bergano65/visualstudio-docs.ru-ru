---
title: "Практическое руководство. Настройка целевых объектов и задач | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>Практическое руководство. Настройка целевых платформ и задач
Некоторые задачи MSBuild можно настроить так, чтобы они выполнялись в целевой среде, независимо от среды на компьютере разработчика. Например, если вы выполняете на 64-разрядном компьютере сборку приложения, предназначенного для 32-разрядной архитектуры, такие задачи можно выполнять в 32-разрядном процессе.  
  
> [!NOTE]
>  Если задача сборки написана на языке .NET, например Visual C# или Visual Basic, и не использует собственные ресурсы и средства, она будет без адаптации выполняться в любом целевом контексте.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>Использование атрибутов и параметров задач  
 Следующие атрибуты `UsingTask` влияют на все операции, выполняемые задачей в конкретном процессе сборки:  
  
-   Атрибут `Runtime`, если указан, задает версию среды выполнения (CLR). Он может принимать любое из следующих значений: `CLR2`, `CLR4`, `CurrentRuntime` или `*` (любая среда выполнения).  
  
-   Атрибут `Architecture`, если указан, задает платформу и разрядность. Он может принимать любое из следующих значений: `x86`, `x64`, `CurrentArchitecture` или `*` (любая архитектура).  
  
-   Атрибут `TaskFactory`, если указан, задает фабрику задач, которая создает и выполняет экземпляр задачи. Он принимает только одно значение: `TaskHostFactory`. Дополнительные сведения см. далее в этой статье в разделе "Фабрики задач".  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Также с помощью параметров `MSBuildRuntime` и `MSBuildArchitecture` можно задать целевой контекст для отдельной задачи.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Перед выполнением задачи MSBuild выполняет поиск соответствующего элемента `UsingTask` с таким же целевым контекстом.  Если параметр задан в элементе `UsingTask`, но не задан в соответствующей задаче, он считается совпадающим.  Если параметр задан в задаче, но не задан в соответствующем элементе `UsingTask`, он также считается совпадающим. Если для параметра не указаны значения ни в `UsingTask`, ни в задаче, для него по умолчанию используется значение `*` (любой параметр).  
  
> [!WARNING]
>  Если существует более одного элемента `UsingTask`, и для каждого из них существуют совпадающие атрибуты `TaskName`, `Runtime` и `Architecture`, принимается тот их них, который был рассмотрен последним.  
  
 Если параметры заданы в задаче, MSBuild пытается найти `UsingTask`, который соответствует этим параметрам или по крайней мере не конфликтует с ними.  Несколько `UsingTask` могут определять целевой контекст для одной задачи.  Например, задача с несколькими исполняемыми файлами для разных целевых сред может выглядеть примерно так:  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Фабрики задач  
 Перед выполнением задачи MSBuild проверяет, предназначена ли она для выполнения в текущем контексте программного обеспечения.  Если задача отмечена как выполнимая, MSBuild передает ее в AssemblyTaskFactory для запуска в текущем процессе. В противном случае MSBuild передает задачу в TaskHostFactory для выполнения в процессе, соответствующем целевому контексту. Даже если текущий контекст соответствует целевому, вы можете принудительно выполнить задачу в отдельном процессе (для изоляции, из соображений безопасности или по другим причинам), указав для параметра `TaskFactory` значение `TaskHostFactory`.  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Фантомные параметры задачи  
 Как и любые другие параметры задачи, `MSBuildRuntime` и `MSBuildArchitecture` можно задать через свойства сборки.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
