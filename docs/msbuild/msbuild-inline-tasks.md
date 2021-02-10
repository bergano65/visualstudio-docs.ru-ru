---
title: Встроенные задачи MSBuild | Документация Майкрософт
description: Узнайте, как создать внутренние задачи MSBuild путем компиляции класса, реализующего интерфейс Microsoft.Build.Framework.ITask.
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
ms.openlocfilehash: 4a90a5a251169bc9b41dea5bfddcfa2f8459af28
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919059"
---
# <a name="msbuild-inline-tasks"></a>Встроенные задачи MSBuild

Задачи MSBuild обычно создаются путем компиляции класса, реализующего интерфейс <xref:Microsoft.Build.Framework.ITask>. Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).

 Начиная с версии 4 .NET Framework, вы можете создавать встроенные задачи в файле проекта. Для размещения задачи не нужно создавать отдельную сборку. Это упрощает как отслеживание исходного кода, так и развертывание задачи. Исходный код встроен в скрипт.

 В MSBuild 15.8 был добавлен [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md), позволяющий создавать кроссплатформенные встроенные задачи .NET Standard.  Если вам нужно использовать встроенные задачи в .NET Core, следует использовать RoslynCodeTaskFactory.
## <a name="the-structure-of-an-inline-task"></a>Структура встроенной задачи

 Элемент [UsingTask](../msbuild/usingtask-element-msbuild.md) содержит встроенную задачу. Встроенная задача и содержащий ее элемент `UsingTask` обычно включены в *TARGETS*-файл и при необходимости импортируются в другие файлы проекта. Ниже представлен пример обычной встроенной задачи. Обратите внимание, что в нем не предусмотрено выполнение каких-либо действий.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="CodeTaskFactory"
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

- Атрибут `AssemblyFile` включает расположение фабрики встроенной задачи. Вы также можете использовать атрибут `AssemblyName` для указания полного имени класса фабрики встроенной задачи, который обычно расположен в `$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll`.

Остальные элементы задачи `DoNothing` пусты и приведены, чтобы показать порядок и структуру встроенной задачи. Более сложный пример представлен в этой статье далее.

- Элемент `ParameterGroup` является необязательным. Если он все же используется, его функция заключается в указании параметров задачи. Дополнительные сведения о входных и выходных параметрах см. в разделе [Входные и выходные параметры](#input-and-output-parameters) ниже.

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

## <a name="helloworld"></a>HelloWorld

 Рассмотрим более сложную встроенную задачу. Задача HelloWorld отображает приветствие "Hello, world!". Оно отображается на устройстве регистрации ошибок по умолчанию. Как правило, это системная консоль или окно **вывода** Visual Studio. В примере элемент `Reference` используется просто для наглядности.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="CodeTaskFactory"
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

Если в элементе `Code` значением атрибута `Type` является `Fragment` или `Method`, тогда свойства для каждого параметра создаются автоматически. В противном случае свойства следует явно объявить в исходном коде задачи. Кроме того, они должны в точности соответствовать определениям своих параметров.

## <a name="example"></a>Пример

 Как показано ниже, встроенная задача заменяет каждое вхождение токена в указанном файле на указанное значение.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup>
      <Path ParameterType="System.String" Required="true" />
      <Token ParameterType="System.String" Required="true" />
      <Replacement ParameterType="System.String" Required="true" />
    </ParameterGroup>
    <Task>
      <Code Type="Fragment" Language="cs"><![CDATA[
string content = File.ReadAllText(Path);
content = content.Replace(Token, Replacement);
File.WriteAllText(Path, content);

]]></Code>
    </Task>
  </UsingTask>

  <Target Name='Demo' >
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>
  </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Пошаговое руководство: Создание встроенной задачи](../msbuild/walkthrough-creating-an-inline-task.md)
