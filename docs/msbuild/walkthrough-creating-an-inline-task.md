---
title: Пошаговое руководство. Создание встроенной задачи | Документация Майкрософт
description: Узнайте, как создать встроенную задачу MSBuild в файле проекта без необходимости создавать отдельную сборку для размещения задачи.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f8a4e39d38f81684b5d090152ec720d45438b3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907462"
---
# <a name="walkthrough-create-an-inline-task"></a>Пошаговое руководство. Создание встроенной задачи

Задачи MSBuild обычно создаются путем компиляции класса, реализующего интерфейс <xref:Microsoft.Build.Framework.ITask>. Начиная с .NET Framework 4, в файле проекта можно создавать встроенные задачи. Для размещения задачи не нужно создавать отдельную сборку. См. дополнительные сведения о [встроенных задачах](../msbuild/msbuild-inline-tasks.md).

 В этом пошаговом руководстве показано, как создать и выполнить следующие встроенные задачи:

- задача, которая не имеет входных или выходных параметров;

- задача, которая имеет один входной параметр и не имеет выходных параметров;

- задача с двумя входными параметрами и одним выходным параметром, возвращающим свойство MSBuild;

- задача с двумя входными параметрами и одним выходным параметром, возвращающим элемент MSBuild.

Чтобы создать и выполнить задачи, следует использовать Visual Studio и **окно командной строки Visual Studio**, как показано ниже.

1. Создайте файл проекта MSBuild с помощью Visual Studio.

2. Измените файл проекта в Visual Studio, чтобы создать встроенную задачу.

3. Используйте **окно командной строки**, чтобы выполнить построение проекта и проверить результаты.

## <a name="create-and-modify-an-msbuild-project"></a>Создание и изменение проекта MSBuild

 Система проектов Visual Studio основана на MSBuild. Поэтому вы можете создать файл проекта построения с помощью Visual Studio. В этом разделе создается файл проекта Visual C#. (Вместо него можно создать файл проекта Visual Basic. В контексте данного руководства различия между двумя файлами проекта незначительны.)

#### <a name="to-create-and-modify-a-project-file"></a>Создание и изменение файла проекта

1. В Visual Studio создайте новый проект с помощью шаблона приложения C# **Windows Forms**. В поле **Имя файла** введите `InlineTasks`. Укажите **расположение** для решения, например *D:\\* . Выберите **Создать каталог для решения**, снимите флажок **Добавить в систему управления версиями**, а для параметра **Имя решения** укажите **InlineTasks**.

3. Нажмите кнопку **ОК**, чтобы создать файл проекта.

3. В **обозревателе решений** щелкните правой кнопкой мыши узел проекта **InlineTasks** и выберите команду **Выгрузить проект**.

4. Еще раз щелкните правой кнопкой мыши узел проекта, а затем выберите **Изменить InlineTasks.csproj**.

     Файл проекта откроется в редакторе кода.

## <a name="add-a-basic-hello-task"></a>Добавление простой задачи Hello

 Теперь добавьте в файл проекта простую задачу, отображающую сообщение "Hello, world!". Также добавьте целевой объект по умолчанию, TestBuild, который будет вызывать задачу.

#### <a name="to-add-a-basic-hello-task"></a>Добавление простой задачи Hello

1. В корневом узле `Project` измените атрибут `DefaultTargets` на `TestBuild`. Итоговый узел `Project` должен выглядеть следующим образом:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Добавьте следующую встроенную задачу и целевой объект в файл проекта непосредственно перед тегом `</Project>`.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Сохраните файл проекта.

   Этот код создает встроенную задачу с именем Hello и не содержит параметров, ссылок или директив `Using`. Задача Hello содержит только одну строку кода, которая отображает сообщение hello в устройстве ведения журнала по умолчанию, обычно в окне консоли.

### <a name="run-the-hello-task"></a>Выполнение задачи Hello

 Запустите MSBuild в **окне командной строки**, чтобы создать задачу Hello и обработать вызывающий ее целевой объект TestBuild.

##### <a name="to-run-the-hello-task"></a>Выполнение задачи Hello

1. Щелкните **Запустить**, **Все программы**, найдите папку **Инструменты Visual Studio** и щелкните **Командная строка Visual Studio**.

2. В **окне командной строки** найдите папку, содержащую файл проекта. В нашем примере это *D:\InlineTasks\InlineTasks\\* .

3. Введите **msbuild** без параметров команды и нажмите клавишу **ВВОД**. По умолчанию в результате создается файл *InlineTasks.csproj* и выполняется обработка стандартного целевого объекта TestBuild, вызывающего задачу Hello.

4. Изучите выходные данные в **окне командной строки**. Вы должны увидеть следующую строку:

    `Hello, world!`

   > [!NOTE]
   > Если вы не видите сообщение hello, повторно сохраните файл проекта и выполните задачу Hello.

   Переключаясь между редактором кода и **окном командной строки**, можно изменять файл проекта и сразу же видеть результаты.

## <a name="define-the-echo-task"></a>Определение задачи Echo

 Создайте встроенную задачу, которая принимает строковый параметр и отображает строку в устройстве ведения журнала по умолчанию.

#### <a name="to-define-the-echo-task"></a>Определение задачи Echo

1. В редакторе кода замените задачу Hello и целевой объект TestBuild, используя следующий код.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. В **окне командной строки** введите **msbuild** без параметров команды и нажмите клавишу **ВВОД**. По умолчанию в результате обрабатывается стандартный целевой объект TestBuild, вызывающий задачу Echo.

3. Изучите выходные данные в **окне командной строки**. Вы должны увидеть следующую строку:

    `Greetings!`

   Этот код определяет встроенную задачу с именем Echo и содержит только один необходимый входной параметр Text. По умолчанию параметры имеют тип System.String. Значение параметра Text задается, когда целевой объект TestBuild вызывает задачу Echo.

## <a name="define-the-adder-task"></a>Определение задачи Adder

 Создайте встроенную задачу, которая добавляет два целочисленных параметра и выдает их сумму в виде свойства MSBuild.

#### <a name="to-define-the-adder-task"></a>Определение задачи Adder

1. В редакторе кода замените задачу Echo и целевой объект TestBuild, используя следующий код.

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. В **окне командной строки** введите **msbuild** без параметров команды и нажмите клавишу **ВВОД**. По умолчанию в результате обрабатывается стандартный целевой объект TestBuild, вызывающий задачу Echo.

3. Изучите выходные данные в **окне командной строки**. Вы должны увидеть следующую строку:

    `The sum is 9`

   Этот код определяет встроенную задачу с именем Adder и содержит два обязательных целочисленных входных параметра, A и B, и один целочисленный выходной параметр C. Задача Adder добавляет два входных параметра и возвращает их сумму в выходном параметре. Сумма выдается в виде свойства MSBuild `Sum`. Значения входных параметров задаются, когда целевой объект TestBuild вызывает задачу Adder.

## <a name="define-the-regx-task"></a>Определение задачи RegX

 Создайте встроенную задачу, которая принимает группу элементов и регулярное выражение и возвращает список всех элементов, содержимое файлов которых соответствует выражению.

#### <a name="to-define-the-regx-task"></a>Определение задачи RegX

1. В редакторе кода замените задачу Adder и целевой объект TestBuild, используя следующий код.

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. В **окне командной строки** введите **msbuild** без параметров команды и нажмите клавишу **ВВОД**. По умолчанию в результате обрабатывается стандартный целевой объект TestBuild, вызывающий задачу RegX.

3. Изучите выходные данные в **окне командной строки**. Должны отобразиться следующие строки:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Этот код определяет встроенную задачу с именем RegX и содержит следующие три параметра:

- `Expression` — обязательный строковый входной параметр, где в качестве значения принимается регулярное выражение для сопоставления. В этом примере выражение соответствует словам public или protected.

- `Files` — обязательный строковый входной параметр списка элементов, где в качестве значения принимается список файлов для поиска соответствия. В этом примере для параметра `Files` задан элемент `Compile`, который выводит список исходных файлов проекта.

- `Result` — обязательный выходной параметр, где в качестве значения принимается список файлов, в которых есть содержимое, соответствующее регулярному выражению.

  Значения входных параметров задаются, когда целевой объект TestBuild вызывает задачу RegX. Задача RegX считывает каждый файл и возвращает список файлов, соответствующих регулярному выражению. Этот список возвращается в виде выходного параметра `Result`, который выдается как элемент MSBuild `MatchedFiles`.

### <a name="handle-reserved-characters"></a>Использование зарезервированных знаков

 Средство синтаксического анализа MSBuild обрабатывает встроенные задачи как XML-файлы. Знаки с зарезервированным значением в XML, например \<" and ">, обнаруживаются и обрабатываются, как если бы они были в формате XML, а не в формате исходного кода .NET. Чтобы включать зарезервированные знаки в выражениях кода, таких как `Files.Length > 0`, напишите элемент `Code`, чтобы его содержимое было включено в выражение CDATA, следующим образом:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>См. также

- [Встроенные задачи](../msbuild/msbuild-inline-tasks.md)
- [Задачи](../msbuild/msbuild-tasks.md)
- [Целевые объекты](../msbuild/msbuild-targets.md)
