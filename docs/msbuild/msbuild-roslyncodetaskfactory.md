---
title: Встроенные задачи MSBuild с RoslynCodeTaskFactory | Документы Майкрософт
description: Сведения о фабрике RoslynCodeTaskFactory MSBuild, которая использует кроссплатформенные компиляторы Roslyn для создания сборок задач в памяти, используемых в качестве встроенных задач.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c033c4d0ee36b9cb01618dd3ac3183e8782c70d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878426"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Встроенные задачи MSBuild с RoslynCodeTaskFactory

Аналогично [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory использует кроссплатформенные компиляторы Roslyn для создания сборок задач в памяти, используемых в качестве встроенных задач.  Задачи RoslynCodeTaskFactory ориентированы на .NET Standard и могут работать в средах выполнения .NET Framework и .NET Core, а также на других платформах, таких как Linux и Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory есть в MSBuild начиная с версии 15.8. Версии MSBuild соответствуют версиям Visual Studio, поэтому RoslynCodeTaskFactory предоставляется в Visual Studio 2017 версии 15.8 и выше.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Структура встроенной задачи с RoslynCodeTaskFactory

 Встроенные задачи RoslynCodeTaskFactory объявляются так же, как [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md). Единственное отличие заключается в том, что они ориентированы на .NET Standard.  Встроенная задача и содержащий ее элемент `UsingTask` обычно включены в *TARGETS*-файл и при необходимости импортируются в другие файлы проекта. Ниже представлен пример обычной встроенной задачи. Обратите внимание, что в нем не предусмотрено выполнение каких-либо действий.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 Элемент `UsingTask` в примере включает три атрибута, описывающих задачу и фабрику встроенной задачи, компилирующую ее.

- Атрибут `TaskName` содержит имя задачи. В примере используется имя — `DoNothing`.

- Атрибут `TaskFactory` содержит класс, реализующий фабрику встроенной задачи.

- Атрибут `AssemblyFile` включает расположение фабрики встроенной задачи. Вы также можете использовать атрибут `AssemblyName` для указания полного имени класса фабрики встроенной задачи, который обычно расположен в глобальном кэше сборок (GAC).

Остальные элементы задачи `DoNothing` пусты и приведены, чтобы показать порядок и структуру встроенной задачи. Более сложный пример представлен в этой статье далее.

- Элемент `ParameterGroup` является необязательным. Если он все же используется, его функция заключается в указании параметров задачи. Дополнительные сведения о входных и выходных параметрах см. в разделе [Входные и выходные параметры](#input-and-output-parameters) далее в этой статье.

- Элемент `Task` содержит исходный код задачи и описывает его.

- Элемент `Reference` указывает ссылки на сборки .NET, используемые в коде. Это эквивалентно добавлению ссылки в проект в Visual Studio. Атрибут `Include` задает путь к сборке, на которую указывает ссылка.

- Элемент `Using` необходим для вывода списка пространств имен, к которым нужно получить доступ. Он похож на оператор `Using` в Visual C#. Атрибут `Namespace` указывает пространство имен, которое нужно включить.

Элементы `Reference` и `Using` подходят для любого языка. Встроенные задачи можно написать на любом из поддерживаемых языков .NET CodeDom, например Visual Basic или Visual C#.

> [!NOTE]
> Элементы, содержащиеся в элементе `Task`, характерны для фабрики задачи, в этом случае для фабрики кода задачи.

### <a name="code-element"></a>Code, элемент

Последний дочерний элемент в элементе `Task` — `Code`. Элемент `Code` содержит код, который нужно скомпилировать в задачу, или определяет его местонахождение. Содержимое в элементе `Code` зависит от того, каким образом вы хотите написать задачу.

Атрибут `Language` указывает язык, на котором написан код. Допустимые значения: `cs` для C# и `vb` для Visual Basic.

Атрибут `Type` указывает тип кода, находящийся в элементе `Code`.

- Если значением атрибута `Type` является `Class`, элемент `Code` содержит код для класса, производного от интерфейса <xref:Microsoft.Build.Framework.ITask>.

- Если значением атрибута `Type` является `Method`, код определяет переопределение метода `Execute` интерфейса <xref:Microsoft.Build.Framework.ITask>.

- Если значением атрибута `Type` является `Fragment`, тогда код определяет содержимое метода `Execute`, а не сигнатуру или оператор `return`.

Сам код отображается, как правило, между метками `<![CDATA[` и `]]>`. Так как код размещается в разделе CDATA, вам не нужно беспокоиться об экранировании зарезервированных знаков, например \<" or ">.

Вы также можете использовать атрибут `Source` элемента `Code`, чтобы указать расположение файла, содержащего код для задачи. Код в исходном файле должен иметь тип, заданный атрибутом `Type`. Если есть атрибут `Source`, тогда по умолчанию значением атрибута `Type` является `Class`. Если атрибут `Source` отсутствует, значением по умолчанию будет `Fragment`.

> [!NOTE]
> При определении класса задачи в исходном файле имя класса должно быть согласовано с атрибутом `TaskName` соответствующего элемента [UsingTask](../msbuild/usingtask-element-msbuild.md).

## <a name="hello-world"></a>Hello World

 Здесь приведена более сложная встроенная задача с RoslynCodeTaskFactory. Задача HelloWorld отображает приветствие "Hello, world!". Оно отображается на устройстве регистрации ошибок по умолчанию. Как правило, это системная консоль или окно **вывода** Visual Studio. В примере элемент `Reference` используется просто для наглядности.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

Задачу HelloWorld можно сохранить в файл с именем *HelloWorld.targets*, а затем вызвать его из проекта, как показано ниже.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Входные и выходные параметры

 Параметры встроенной задачи являются дочерними элементами элемента `ParameterGroup`. Каждый параметр принимает имя элемента, который его определяет. Код, представленный ниже, определяет параметр `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Параметры могут иметь один или несколько атрибутов:

- Атрибут `Required` является необязательным и по умолчанию имеет значение `false`. Если же используется значение `true`, тогда этот параметр обязателен и перед вызовом задачи ему необходимо присвоить значение.

- Атрибут `ParameterType` является необязательным и по умолчанию имеет значение `System.String`. Вы можете его задать для любого полного типа, являющегося элементом или значением, которые можно преобразовать как в строку, так и из нее, используя System.Convert.ChangeType. Другими словами, любой тип, который можно передать во внешнюю задачу или же из нее.

- Атрибут `Output` является необязательным и по умолчанию имеет значение `false`. Если же используется значение `true`, тогда этому параметру необходимо присвоить значение перед возвратом из метода Execute.

Например, примененная к объекту директива

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

определяет следующие три параметра:

- `Expression` является обязательным входным параметром типа System.String.

- `Files` является обязательным входным параметром списка элементов.

- `Tally` является выходным параметром типа System.Int32.

Если в элементе `Code` значением атрибута `Type` является `Fragment` или `Method`, тогда свойства для каждого параметра создаются автоматически.  Если в RoslynCodeTaskFactory элемент `Code` имеет атрибут `Type` со значением `Class`, атрибут `ParameterGroup` указывать не нужно, так как он выводится из исходного кода (в отличие от `CodeTaskFactory`). В противном случае свойства следует явно объявить в исходном коде задачи. Кроме того, они должны в точности соответствовать определениям своих параметров.

## <a name="example"></a>Пример

 Следующая встроенная задача регистрирует некоторые сообщения и возвращает строку.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Эти встроенные задачи могут комбинировать пути и получать имя файла.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Обеспечение обратной совместимости

`RoslynCodeTaskFactory` предоставляется, начиная с MSBuild версии 15.8. Предположим, вам требуется реализовать поддержку предыдущих версий Visual Studio и MSBuild, когда `RoslynCodeTaskFactory` не предоставляется, а `CodeTaskFactory` предоставляется, но вы хотите использовать тот же скрипт сборки. Вы можете использовать конструкцию `Choose` со свойством `$(MSBuildVersion)`, чтобы определить, следует ли использовать `RoslynCodeTaskFactory` или `CodeTaskFactory`, как показано в следующем примере.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Пошаговое руководство: Создание встроенной задачи](../msbuild/walkthrough-creating-an-inline-task.md)
