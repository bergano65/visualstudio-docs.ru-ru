---
title: Написание задач | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9701497def997b96eff50b0713bc3e16a97f63d
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483865"
---
# <a name="task-writing"></a>Написание задач
Задачи содержат код, который выполняется в процессе сборки. Задачи содержатся в целевых объектах. В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] включена библиотека типичных задач, но также можно создавать собственные задачи. Дополнительные сведения о библиотеке задач, включенных в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], см. в статье [Справочные сведения о задачах MSBuild](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Задачи  
 Примеры задач: [Copy](../msbuild/copy-task.md) — копирование одного или нескольких файлов; [MakeDir](../msbuild/makedir-task.md) — создание каталога; [Csc](../msbuild/csc-task.md) — компиляция файлов исходного кода [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Каждая задача реализуется в виде класса платформы .NET, реализующего интерфейс <xref:Microsoft.Build.Framework.ITask>, который определяется в сборке *Microsoft.Build.Framework.dll*.  
  
 Существуют два подхода к реализации задачи:  
  
-   Прямая реализация интерфейса <xref:Microsoft.Build.Framework.ITask>.  
  
-   Произведите класс от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>, который определен в сборке *Microsoft.Build.Utilities.dll*. Задача реализует интерфейс ITask и обеспечивает реализации по умолчанию некоторых элементов ITask. Кроме того, упрощается ведение журнала.  

В обоих случаях необходимо добавить в свой класс метод `Execute`, то есть метод, который вызывается при выполнении задачи. Этот метод не принимает параметров и возвращает значение типа `Boolean`: `true`, если задача успешно выполнена, или `false`, если задачу выполнить не удалось. В приведенном ниже примере показана задача, не выполняющая никакого действия и возвращающая значение `true`.  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Эта задача запускается из следующего файла проекта:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Если свойства .NET создаются в классе задач, то выполняющиеся задачи могут получать входные данные из файла проекта. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] задает эти свойства непосредственно перед вызовом метода `Execute` задачи. Чтобы создать свойство строки, используйте код задачи следующего вида:  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
  
        public string MyProperty { get; set; }
    }  
}  
```  
  
 Следующий файл проекта запускает эту задачу и присваивает свойству `MyProperty` указанное значение:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="register-tasks"></a>Регистрация задач  
 Если проекту предстоит запускать задачу, платформе [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] необходимо знать, как найти сборку, содержащую класс задачи. Задачи регистрируются с помощью [элемента UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 Файл [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] в `UsingTask`Microsoft.Common.Tasks[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] — это файл проекта, который содержит список элементов *, регистрирующих все задачи, предоставленные в* . Этот файл включается автоматически при сборке каждого проекта. Если задача, зарегистрированная в *Microsoft.Common.Tasks*, зарегистрирована также в текущем файле проекта, текущий файл проекта имеет приоритет. Таким образом можно переопределить задачу по умолчанию собственной задачей с тем же именем.  
  
> [!TIP]
>  Чтобы увидеть список задач, включенных в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], просмотрите содержимое файла *Microsoft.Common.Tasks*.  
  
## <a name="raise-events-from-a-task"></a>Создание событий из задачи  
 Если задача является производной от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>, вы можете использовать любой из следующих вспомогательных методов класса <xref:Microsoft.Build.Utilities.Task> для создания событий, которые будут перехватываться и отображаться зарегистрированными средствами ведения журнала:  
  
```csharp
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Если задача реализует интерфейс <xref:Microsoft.Build.Framework.ITask> напрямую, вы также можете создавать эти события, но необходимо использовать интерфейс IBuildEngine. В следующем примере показана задача, реализующая интерфейс ITask и создающая пользовательское событие:  
  
```csharp
public class SimpleTask : ITask  
{  
    public IBuildEngine BuildEngine { get; set; }
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## <a name="require-task-parameters-to-be-set"></a>Обязательные параметры задачи  
 Некоторые свойства задачи можно пометить как "обязательные", чтобы в любом файле проекта, из которого запускается задача, значения этих свойств должны были быть заданы, чтобы сборка не завершилась сбоем. Примените к свойству .NET в задаче атрибут `[Required]` следующим образом:  
  
```csharp
[Required]  
public string RequiredProperty { get; set; }
```  
  
 Атрибут `[Required]` определяется классом <xref:Microsoft.Build.Framework.RequiredAttribute> в пространстве имен <xref:Microsoft.Build.Framework>.  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В этом классе [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] показана задача, производная от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>. Эта задача возвращает значение `true`, указывающее на успешное выполнение.  
  
### <a name="code"></a>Код  
  
```csharp
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В этом классе [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] показана задача, реализующая интерфейс <xref:Microsoft.Build.Framework.ITask>. Эта задача возвращает значение `true`, указывающее на успешное выполнение.  
  
### <a name="code"></a>Код  
  
```csharp
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        public IBuildEngine BuildEngine { get; set; }
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type object.  
        // This is done for you if you derive from the Task class.  
        public object HostObject { get; set; }
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В этом классе [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] показана задача, производная от вспомогательного класса <xref:Microsoft.Build.Utilities.Task>. В ней задается обязательное строковое свойство и создается событие, отображаемое всеми зарегистрированными средствами ведения журнала.  
  
### <a name="code"></a>Код  
 [!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В этом примере показан файл проекта, в котором вызывается задача из предыдущего примера (SimpleTask3).  
  
### <a name="code"></a>Код  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
