---
title: Практическое руководство. Настройка целевых объектов и задач | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a09f2ec1af511cb789f2101e2df0a675dd065e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
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
```  
  
 В отличие от других параметров задач, `MSBuildRuntime` и `MSBuildArchitecture` не очевидны для самой задачи.  Чтобы написать задачу, учитывающую контекст, в котором она выполняется, нужно проверить контекст, вызвав платформу .NET Framework, либо использовать свойства сборки для передачи сведений о контексте через другие параметры задачи.  
  
> [!NOTE]
>  Атрибуты `UsingTask` можно задать из набора инструментов и свойств среды.  
  
 Параметры `MSBuildRuntime` и `MSBuildArchitecture` предоставляют самый гибкий способ задать целевой контекст, но при этом имеют наиболее ограниченную область действия.  С одной стороны, так как они задаются для самого экземпляра задачи и не вычисляются до выполнения задачи, они могут наследовать свои значения от полного набора свойств, доступных во время вычисления и построения.  С другой стороны, эти параметры применяются только к определенному экземпляру задачи в конкретном целевом объекте.  
  
> [!NOTE]
>  Параметры задачи вычисляются в контексте родительского узла, а не в контексте узла задач. Переменные среды, которые зависят от среды выполнения или архитектуры (например, как расположение "Program files"), будут вычисляться в значение, соответствующее родительскому узлу.  Но если та же самая переменная среды считывается непосредственно задачей, она корректно вычисляется в контексте узла задачи.  
  
## <a name="see-also"></a>См. также  
 [Настройка целевых платформ и задач](../msbuild/configuring-targets-and-tasks.md)
