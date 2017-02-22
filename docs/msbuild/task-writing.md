---
title: "Написание задач | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, создание задач"
  - "MSBuild, запись задач"
  - "задачи, создание для MSBuild"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Написание задач
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В задачах предоставляется код, выполняющийся во время процесса построения.  Задания содержатся в целях.  В [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] включена библиотека типичных задач, а также можно создавать собственные задачи.  Дополнительные сведения о библиотеке задач, включенных в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], см. в разделе [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md).  
  
## Задачи  
 Примеры задач: [Copy](../msbuild/copy-task.md) — копирование одного или нескольких файлов, [MakeDir](../msbuild/makedir-task.md) — создание каталога, [Csc](../msbuild/csc-task.md) — компиляция файлов исходного кода [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Каждая задача реализована в виде класса платформы .NET, обеспечивающего интерфейс <xref:Microsoft.Build.Framework.ITask>, который определен в сборке Microsoft.Build.Framework.dll.  
  
 Существуют два подхода к реализации задачи.  
  
-   Реализация непосредственно интерфейса <xref:Microsoft.Build.Framework.ITask>.  
  
-   Получение класса из вспомогательного класса <xref:Microsoft.Build.Utilities.Task>, который определен в сборке Microsoft.Build.Utilities.dll.  Задача реализует ITask и обеспечивает реализации по умолчанию некоторых элементов ITask.  Кроме того, упрощается ведение журнала.  
  
 В обоих случаях необходимо добавить в свой класс метод с названием `Execute`, то есть метод, который вызывается при выполнении задачи.  Этот метод не получает никаких параметров и возвращает значение `Boolean`: `true`, если задача успешно выполнена, или `false`, если задачу выполнить не удалось.  В следующем примере показана задача, не выполняющая никакого действия и возвращающая значение `true`.  
  
```  
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
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Если свойства .NET создаются в классе задач, то выполняющиеся задачи могут получать входные данные из файла проекта.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] задает эти свойства непосредственно перед вызовом метода `Execute`.  Чтобы создать свойство строки, используйте код задачи следующего вида:  
  
```  
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
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Из следующего файла проекта запускается эта задача и задается свойство `MyProperty` для заданного значения:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## Регистрация задач  
 Если проекту предстоит запускать задачу, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] необходимо знать, как найти сборку, содержащую класс задачи.  Задачи регистрируются с использованием метода [Элемент UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
 Файл Microsoft.Common.Tasks в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] — это файл проекта, который содержит список элементов `UsingTask`, регистрирующих все задачи, предоставленные вместе с [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Этот файл включается автоматически при создании каждого проекта.  Если задача, зарегистрированная в файле Microsoft.Common.Tasks, зарегистрирована также в текущем файле проекта, текущий файл проекта имеет преимущество; таким образом можно переопределить задачу по умолчанию собственной задачей с тем же именем.  
  
> [!TIP]
>  Чтобы увидеть список задач, предоставленных вместе с [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], просмотрите содержимое файла Microsoft.Common.Tasks.  
  
## Создание событий из задачи  
 В случае получения задачи из вспомогательного класса <xref:Microsoft.Build.Utilities.Task> можно использовать любой из следующих вспомогательных методов в классе <xref:Microsoft.Build.Utilities.Task> для создания событий, которые будут подхватываться и отображаться каким\-либо зарегистрированным средством ведения журнала:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Если в задаче реализуется непосредственно интерфейс <xref:Microsoft.Build.Framework.ITask>, можно также создавать эти события, но необходимо использовать интерфейс IBuildEngine.  В следующем примере показана задача, реализующая ITask и создающая пользовательское событие:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
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
  
## Обязательные параметры задачи  
 Некоторые свойства задачи можно пометить как "обязательные", чтобы в любом файле проекта, из которого запускается задача, необходимо было задавать значения для этих свойств, иначе построение выполнить не удастся.  Примените к свойству .NET в задаче атрибут `[Required]` следующим образом:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 Атрибут `[Required]` определен свойством <xref:Microsoft.Build.Framework.RequiredAttribute> в пространстве имен <xref:Microsoft.Build.Framework>.  
  
## Пример  
  
### Описание  
 В этом классе [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] показана задача, получаемая из вспомогательного класса <xref:Microsoft.Build.Utilities.Task>.  Эта задача возвращает значение `true`, указывающее на успешность ее выполнения.  
  
### Код  
  
```  
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
  
## Пример  
  
### Описание  
 В этом классе [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] показана задача, реализующая интерфейс <xref:Microsoft.Build.Framework.ITask>.  Эта задача возвращает значение `true`, указывающее на успешность ее выполнения.  
  
### Код  
  
```  
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
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Пример  
  
### Описание  
 В этом классе [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] показана задача, получаемая из вспомогательного класса <xref:Microsoft.Build.Utilities.Task>.  В ней задается обязательное свойство строки и создается событие, отображаемое всеми зарегистрированными средствами ведения журнала.  
  
### Код  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## Пример  
  
### Описание  
 В этом примере показан файл проекта, в котором вызывается задача из предыдущего примера \(SimpleTask3\).  
  
### Код  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)